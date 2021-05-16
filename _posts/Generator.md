# Generator

> 코드 블록의 실행을 일시 중지했다가 필요한 시점에 재개할 수 있는 함수
> 
> 호출하면 제너레이터 객체를 생성해서 반환한다.

```javascript
function* genFunc() {
    yield 1;
    yield 2;
    yield 3;
}

cont generator = genFunc();

console.log(generator.next()); // iterable, iterator
console.log(generator.next());
console.log(generator.next());
console.log(generator.next()); // done
```

이렇게는 잘 안 쓴다...

### Runner

참조 : [Generator in Practice](https://meetup.toast.com/posts/93)

generator 객체를 받고 처리할 수 있는 Runner 함수를 따로 만들어서 사용한다.

```javascript
function runner(gen) {
    const iter = gen();

    console.log('runner start');

    (function iterate({ value, done }) {

        console.log(value);
        console.log(done);

        if (done) {
            return value;
        }

        if (typeof value === 'number') {
            iterate(iter.next(value * 2));
        } else {
            iterate(iter.next('not a number : ' + value));
        }
    })(iter.next());
}

function* twoTimesNumber() {
    let y = yield 10
    console.log(y);
    y = yield y;
    console.log(y);
    console.log(yield 'hello');
}

runner(twoTimesNumber);
```

### Runner + Promise

```javascript
function run(gen, post_id) {
    const iter = gen(post_id);

    (function iterate({ value, done }) {
        if (done) {
            return value;
        }

        if (value.constructor === Promise) {
            value.then(data => iterate(iter.next(data)));
        } else {
            iterate(iter.next(value));
        }
    })(iter.next());
}

function* getLatestData(post_id) {

    const url = 'https://jsonplaceholder.typicode.com';

    let promise1 = createGetPromise(`${url}/posts/${post_id}`);

    const data1 = yield promise1;

    console.log(data1);

    let promise2 = createGetPromise(`${url}/users/${data1.userId}`)

    const data2 = yield promise2;

    console.log(data2);
}

function createGetPromise(url) {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();
        xhr.open(`GET`, url);
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

run(getLatestData, 2);
```

### Async / Await

위의 코드를 async / await + fetch 로 바꾸면...

```javascript
async function getUserByPostId(post_id) {

    const url = 'https://jsonplaceholder.typicode.com';

    const response_post = await fetch(`${url}/posts/${post_id}`);

    const json_post = await response_post.json();

    const response_user = await fetch(`${url}/users/${json_post.userId}`);

    const json_user = await response_user.json();

    return json_user;

}

const user = getUserByPostId(1);

user.then(console.log);
console.log(user);
```
