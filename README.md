# X-JSON

A dependently typed programming language embedded in JSON,
that can be used as a schema checker for JSON data.

The syntax is optimized for _the most used use cases_.

Instead of writing (like in [json-schema](https://json-schema.org/understanding-json-schema/index.html)):

```json
{
  "type": "object",
  "properties": {
    "year": { "type": "number" },
    "name": { "type": "string" }
  }
}
```

I want to write:

```json
{
  "name": "string",
  "year": "number"
}
```

## Install

```bash
npm i @xieyuheng/x-json
```

## Contributions

To make a contribution, fork this project and create a pull request.

Please read the [STYLE-GUIDE.md](STYLE-GUIDE.md) before you change the code.

Remember to add yourself to [AUTHORS](AUTHORS).
Your line belongs to you, you can write a little
introduction to yourself but not too long.

## License

[GPLv3](LICENSE)
