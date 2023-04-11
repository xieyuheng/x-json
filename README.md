# X Schema

A runtime schema for JSON data, where the syntax is optimized for _the most used use cases_.

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
npm i @xieyuheng/x-schema
```

## Contributions

> Be polite, do not bring negative emotion to others.

- [TODO.md](TODO.md)
- [STYLE-GUIDE.md](STYLE-GUIDE.md)
- [CODE-OF-CONDUCT.md](CODE-OF-CONDUCT.md)
- When contributing, add yourself to [AUTHORS](AUTHORS)

## License

- [GPLv3](LICENSE)
