# Pool Categories

## Adding a new category

To add a new category, add a new object to the `index.json` file that conforms
to the following schema:

```ts
{
  id: string,
  name: string,
  description: string,
  url?: string,
  file?: string // name of file in this directory with list of pool ids
  iconFile?: string // name of file in /icons directory
}
```

Then to associate pools with this category create a file in this directory with
the ID of the category as it's name, e.g. my_category_id.json. The file should
contain a list of pool ids.

## Adding a category icon

To add an icon to be used for a category, add a new file to the /icons directory with
the ID of the category as it's name, e.g. my_category_id.svg. Then add the
`iconFile` property to the category object in `index.json`.
