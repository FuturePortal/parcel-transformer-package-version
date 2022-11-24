# Parcel v2 transformer: package version

If you need to use the package version of your package.json in your project, you can add this transformer to your
project. `PACKAGE_VERSION` will be replaced with the version in your `package.json`.

## Setup

In your `.pracelrc`, add the `@futureportal/parcel-transformer-package-version` transformer for the files you want use the
package version in. In the example below we would like to use the package version in a `.tsx` file and a `.json` file:

```pracelrc
{
	"extends": "@parcel/config-default",
	"transformers": {
		"*.{ts,tsx}": ["@futureportal/parcel-transformer-package-version", "..."],
		"*.{json}": ["@futureportal/parcel-transformer-package-version", "..."],
	}
}
```

Add the `@futureportal/parcel-transformer-package-version` package to your package.json with either yarn or npm.

Now, `PACKAGE_VERSION` will be replaced in the compiled code for the given file transformers.

**Note:** If you don't see any changes, remove your `.parcel-cache` folder and rebuild.

## Typescript example

`src/pages/about.tsx`:

```tsx
import { ReactElement } from 'react';

const About = (): ReactElement => <h1>About version PACKAGE_VERSION</h1>;

export default About;
```

`package.json`:

```json
{
	"version": "1.2.3"
}
```

Will output:

```html
<h1>About version 1.2.3</h1>
```

## JSON example

`src/manifest.json`:

```json
{
	"name": "My application",
	"version": "PACKAGE_VERSION",
	"description": "This is my application vPACKAGE_VERSION"
}
```

`package.json`:

```json
{
	"version": "1.2.3"
}
```

Will output:

```json
{
	"name": "My application",
	"version": "1.2.3",
	"description": "This is my application v1.2.3"
}
```
