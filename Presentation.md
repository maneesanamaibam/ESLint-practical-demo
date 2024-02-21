1. TOP 10 ESLint rules
2. Prettier and ESLint (ESLint Old v8.22.0) [latest v 8.56.0] conflict

### Examples of analyzing eslint errors

Decision context:

1. Code -- what is wrong with my code ?
2. Is the conflicting with prettier/other rules?
3. Is the rule fixable ?
4. Before completely turning off the rule : -- what good things we have compromised and what are the other options we can do ?

### Prettier (arrow-body-style) conflict

### Tips

- Maintain consistent pace of speaking
- Let audience chase the solution

### Top 10 ESLint rules

1.  require-array-sort-compare
2.  no-prototype-builtins
3.  no-unmodified-loop-condition
4.  no-implied-eval
5.  prefer-optional-chain
6.  no-await-in-loop
7.  prefer-nullish-coalescing
8.  no-array-delete
9.  consistent-type-definitions
10. no-unnecessary-boolean-literal-compare


### Top 10 code examples
```typescript
// 1.  require-array-sort-compare
//
// BAD CODE
const arr: number[] = [132, 234, 13, 64, 35, 16, 37, 78, 9, 10];
arr.sort();
// GOOD CODE
// const arr: number[] = [132, 234, 13, 64, 35, 16, 37, 78, 9, 10];
// const compareFn = (a: number, b: number) => a - b;
// arr.sort(compareFn);

// 2.  no-prototype-builtins
// This rule disallows calling some Object.prototype methods directly on object instances.
// BAD CODE
const foo = {
  baz: "baz",
};
const hasBazProperty = foo.hasOwnProperty("baz");
// GOOD CODE
// const foo = {
//   baz: "baz",
// };
// const hasBazProperty = Object.prototype.hasOwnProperty.call(foo, "baz");

// 3.  no-unmodified-loop-condition
// Variables in a loop condition often are modified in the loop. If not, it’s possibly a mistake.
// BAD CODE
let count = 1;
while (count) {
  console.log(count);
}
count++;
// GOOD CODE
// let count = 1;
// while (count) {
//   console.log(count);
//   count++;
// }

// 4.  no-implied-eval
// BAD CODE
setTimeout("alert('Hi!');", 100);
// GOOD CODE
// setTimeout(() => {
//   alert("Hi!");
// }, 100);
// 5.  prefer-optional-chain
// BAD CODE
const obj = { a: "a" };
const val = obj && obj.a && obj.a.b && obj.a.b.c;

// GOOD CODE
const obj = { a: "a" };
const val = obj?.a?.b?.c;

// 6.  no-await-in-loop
// BAD CODE
async function foo(things) {
  const results = [];
  for (const thing of things) {
    // Bad: each loop iteration is delayed until the entire asynchronous operation completes
    results.push(await bar(thing));
  }
  return baz(results);
}
// GOOD CODE
// async function foo(things) {
//   const results = [];
//   for (const thing of things) {
//     // Good: all asynchronous operations are immediately started.
//     results.push(bar(thing));
//   }
//   // Now that all the asynchronous operations are running, here we wait until they all complete.
//   return baz(await Promise.all(results));
// }

// 7.  prefer-nullish-coalescing
// 8.  no-array-delete
// 9.  consistent-type-definitions
// 10. no-unnecessary-boolean-literal-compare
```
