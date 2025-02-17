# API Client for paperless-ng

## Installation

```bash
# yarn
yarn install paperless

# NPM
npm install paperless
```

## Usage

Here are some examples how this library works. Since it is fully typed I won't explain every method here. Just dive into the types and you're ready to roll. Also note that not all functions are available right now. Mostly GET functions work.

```ts
import { Paperless } from 'paperless';

const paperless = new Paperless({
  username: 'dunklestoast',
  password: 'mucho_secret',
  host: 'paperless.example.com',
  port: 1337,
});

// Get a document by Id
const document = await paperless.getDocument(2);

// Get a filtered list of documents where title or content contains the word Rechnung
const result = await paperless.getDocuments({title_content: "Rechnung"})
console.log(result);

// with Ordering
const document = await paperless.getDocuments({title_content: "Rechnung24165"},{ordering: TITLE_ASCENDING})
console.log(document);

// Get a filtered list of tags with name starts with to
const result = await paperless.getTags({name__istartswith: "in"})
console.log(result);

// Download a document
const file = await paperless.downloadDocument(2);
fs.writeFileSync(`${document.title}.pdf`, file);

// Get a documents thumbnail
await paperless.getThumbnail(2);
```

## React Native

This package is compatible with React Native. However, the `ignoreSSL` feature is not supported and will throw errors, if you set this to true. 
