# Phonetic Transcription Lessons

## callback

```javascript
getUser(user => {
  getRepositories(user, repos => {
    getIssues(repos, issues => {
      getReplies(issues, () => {
        ...
      })
    })
  })
});
```

- callback hell

## thunk

```js
function add5(a) {
  return a + 5
}

var b = 7
add5(1+ b)
```

- thunkify

```js
fs.readFile('/etc/passwd', 'utf8', callback);

read = thunkify(fs.readFile)

read('/etc/xxx', 'utf8')(function() {});
```

## promise

```js
getUser().then(user => {
  return getRepositories(user);
}).then(repos => {
  return getIssues(repos);
}).then(issues => {
  return getReplies(issues)
}).then(replies => {
  ...
}).catch(err => {
  ...
});
```

a. catch
getUser().then(...).catch(...);

b. all
c. race
d. resolve/reject

```js
var p1 = new Promise((resolve, reject) => {

});
```


## generator

```js
function* idMaker() {
  var index = 0;
  while (index < 3)
    yield index++;
}

var gen = idMaker();

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // undefined
// ...
```

## co

```javascript
co(function *() {
  try {
    var user = yield getUser();
    var repos = yield getRepositories(user);
    var issues = yield getIssues(repos);
    var replies = yield getReplies(issues);
  } catch(err => {
    console.log(err);
  })
});
```

## async & await

```javascript
async function test() {
  try {
    var user = await getUser();
    var repos = await getRepositories(user);
    var issues = await getIssues(repos);
    var replies = await getReplies(issues);
  } catch(err) {
    console.log(err);
  }
}
```


## License

Powered by xiad © 2017, `jiubao`
