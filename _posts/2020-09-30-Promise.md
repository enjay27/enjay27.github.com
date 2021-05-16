# Promise

> 비동기함수 : 비동기로 동작하는 코드를 포함한 함수

비동기 함수를 호출하면 함수 내부의 비동기로 동작하는 코드가 완료되지 않았다 해도 기다리지 않고 즉시 종료된다.

1. 함수 호출
2. 함수 실행
3. 함수 종료
4. 종료 이후에 함수 내부의 비동기 동작 코드 실행

따라서 비동기로 동작하는 코드의 처리 결과를 얻어야 하는 경우 기대한 대로 동작하지 않게 된다.

```javascript
let todos;

const get = url => {
    const xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.send();

    xhr.onload = () => {
        if (xhr.status === 200) {
            todos = JSON.parse(xhr.response);
        } 
        console.error(`${xhr.status} ${xhr.statusText}`);
    };
};

get('https://jsonplaceholder.typicode.com/posts/1');
console.log(todos);
```

1. get 실행 -> onload binding  
2. get 종료 -> console.log 실행
3. 서버로부터 응답 도착 -> xhr에서 load 이벤트 발생
4. 태스크 큐에 저장된 후 __콜 스택이 비면__ 콜 스택에 푸시되어 실행된다.

비동기 함수 내부의 처리 결과는 이처럼 외부에 반환할 수 없고, 상위 스코프의 변수에 할당할 수도 없다.

비동기 함수의 처리 결과에 대한 후속 처리는 비동기 함수 내부에서 수행해야 한다.

### 비동기 함수 내부에서 처리하기

```javascript
const get = (url, successCallback, failureCallback) => {
    const xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.send();

    xhr.onload = () => {
        if (xhr.status === 200) {
            successCallback(JSON.parse(xhr.response));
        } else {
            failureCallback(xhr.status);
        }
    };
};

const response = get(
    'https://jsonplaceholder.typicode.com/posts/1',
    console.log, console.error);
```

함수를 파라미터로 넘겨서 비동기 함수 내부에서 console.log 처리를 했다.

> callback hell : 후속 처리를 수행하는 비동기 함수고 처리 결과를 가지고 비동기 함수를 호출해야 한다면 복잡도가 높아지는 현상이 발생한다.

![callback hell](https://i.ytimg.com/vi/fr67u98nckk/maxresdefault.jpg)

### 에러처리?

콜백 패턴은 에러 처리가 불가능하다.

```javascript
try {
    setTimeout(() => {throw new Error('Error'); }, 1000);
} catch (e) {
    console.error('error', e);
}
```

여기서 setTimeout 내부의 콜백함수는 에러를 발생시킨다. 하지만 catch문은 setTimeout 함수의 에러만 체크하고, setTimeout 함수는 에러 없이 정상적인 동작을 했기 때문에 에러 처리를 하지 못한다.

이후 콜백함수가 실행될 때 에러가 발생하고, 처리가 불가능하게 된다.

## Promise 도입

Promise 생성자 함수는 비동기 처리를 수행할 콜백 함수를 파라미터로 받는데 이 콜백 함수는 resolve와 reject 함수를 파라미터로 받는다.

```javascript
const promiseGet = url => {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();
        xhr.open('GET', url);
        xhr.send();

        xhr.onload = () => {
            if (xhr.status === 200) { 
                resolve(JSON.parse(xhr.response));
            } else {
                reject(new Error(xhr.status));
            }
        };
    });
}

promiseGet('https://jsonplaceholder.typicode.com/posts/1');
```

promise의 상태

- pending : 비동기 처리가 아직 수행되지 않은 상태
- fulfiled : 비동기 처리가 수행되고 성공한 상태
- rejected : 비동기 처리가 수행되고 실패한 상태

생성 직후인 pending 상태에서 resolve 함수 혹은 reject 함수를 호출하면 상태가 바뀐다.

### Promise 후속 처리

```javascript
const promiseGet = url => {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();
        xhr.open('GET', url);
        xhr.send();

        xhr.onload = () => {
            if (xhr.status === 200) { 
                resolve(JSON.parse(xhr.response));
            } else {
                reject(new Error(xhr.status));
            }
        };
    });
}

promiseGet('https://jsonplaceholder.typicode.com/posts/1')
    .then(v => console.log(v))
    .catch(e => console.log(e))
    .finally(() => console.log('Completed'));
```

- then : 두 개의 콜백 함수를 넘기고 후속 처리에 대한 결과를 이용하여 콜백 함수를 실행한다... 두번째는 에러 처리 함수이기 때문에 하나만 넘긴다.

- catch : 한 개의 콜백 함수를 넘기고 에러 처리를 실행한다.

- finally : 한 개의 콜백 함수를 넘기고 성공, 실패 여부와 상관없이 콜백 함수를 실행한다.

### Promise Chaining

```javascript
const promiseGet = url => {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();
        xhr.open('GET', url);
        xhr.send();

        xhr.onload = () => {
            if (xhr.status === 200) { 
                resolve(JSON.parse(xhr.response));
            } else {
                reject(new Error(xhr.status));
            }
        };
    });
}

const url = 'https://jsonplaceholder.typicode.com';

promiseGet(`${url}/posts/1`)
    .then(({ userId }) => promiseGet(`${url}/users/${userId}`))
    .then(userInfo => console.log(userInfo))
    .catch(err => console.error(err));
```

then, catch, finally 메서드가 프로미스를 반환하기 때문에 연속적으로 호출할 수 있다.

catch 는 앞의 promise에서 reject한 값으로 실행된다.

### 정적 메서드들

- resolve, reject : 각각 resolve, reject 하는 Promise 를 생성한다.
- all : 여러 개의 promise를 받아서 한번에 병렬 처리한다.
- race : 여러 개의 promise를 받아서 한번에 병렬 처리하며 하나라도 fulfilled 혹은 rejected 상태가 되면 해당 상태의 프로미스를 반환한다.
- allSettled : 여러 개의 promise를 받고 모든 promise가 settled 상태가 되면 처리 결과를 배열로 반환한다.

### fetch

```javascript
fetch('https://jsonplaceholder.typicode.com/todos/1')
    .then(response => console.log(response));
```

http 응답을 나타내는 response 객체를 래핑한 promise를 반환한다.

자세한건 [Using Fetch](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch) ...
