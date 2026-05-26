# All-True Property Validator

A lightweight JavaScript utility that checks whether **every object** in a collection has a truthy value for a given property key.

---

## Function

```js
function truthCheck(collection, pre) {
  for (let obj of collection) {
    if (!obj[pre]) {
      return false;
    }
  }
  return true;
}
```

---

## How It Works

`truthCheck` iterates over an array of objects and evaluates each object's value at the key `pre`. If **any** object has a falsy value (e.g. `false`, `""`, `0`, `null`, `undefined`) for that key, the function immediately returns `false`. Only if all objects pass does it return `true`.

---

## Parameters

| Parameter    | Type     | Description                                      |
|--------------|----------|--------------------------------------------------|
| `collection` | `Array`  | An array of objects to check                     |
| `pre`        | `String` | The property key to evaluate on each object      |

**Returns:** `Boolean` — `true` if all objects have a truthy value for `pre`, otherwise `false`.

---

## Example

```js
truthCheck(
  [
    { name: "Quincy",    role: "Founder", isBot: false },
    { name: "Naomi",     role: "",        isBot: false },
    { name: "Camperbot", role: "Bot",     isBot: true  }
  ],
  "isBot"
);
// → false
```

**Why `false`?**
- `Quincy.isBot` → `false` ❌ — immediately short-circuits and returns `false`

---

## More Examples

```js
// All objects have a non-empty "name" → true
truthCheck(
  [{ name: "Alice" }, { name: "Bob" }],
  "name"
);
// → true

// One object has an empty "role" string → false
truthCheck(
  [{ role: "Admin" }, { role: "" }, { role: "User" }],
  "role"
);
// → false

// Property is missing entirely on one object → false
truthCheck(
  [{ active: true }, { active: true }, {}],
  "active"
);
// → false
```

---

## Falsy Values Reference

The following values cause `truthCheck` to return `false`:

| Value       | Type        |
|-------------|-------------|
| `false`     | Boolean     |
| `""`        | String      |
| `0`         | Number      |
| `null`      | Null        |
| `undefined` | Undefined   |
| `NaN`       | NaN         |

---

## Usage

No dependencies. Just copy the function into your project and call it directly.

```js
const result = truthCheck(myCollection, "isActive");
console.log(result); // true or false
```

---

## Contributing

Pull requests and issues are welcome. Please open an issue first to discuss any changes you'd like to make.
