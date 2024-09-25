# Balancer Metadata

Public metadata for the Balancer protocol.

## Categories
Categories are used to tag sets of pools in the [Balancer API](https://github.com/balancer/backend) and [frontend](https://github.com/balancer/frontend-v3).

### Adding new categories
To add a new category, update the [categories json](https://github.com/balancer/metadata/blob/main/pools/categories/index.json) with an object using the following schema:
```ts
type Category = {
  id: string // If it's a points category, prepend id with `points_`, see existing categories for examples.
  name: string
  description: string
  value?: string // Arbitrary value that may be used by the frontend to provide more context, e.g. points multiples for points categories.
  url?: string
  file: string // The file that includes the list of pool IDs that should be associated with this category. Should be a relative path, see existing categories for examples.
  fileIcon?: string // Icon to be used in frontend to represent the category. Should be a relative path, see existing categories for examples.
}
```
To associate your category with a set of pools, add a json file [here](https://github.com/balancer/metadata/tree/main/pools/categories) that includes an array of pool IDs. Then reference that file name in the above schema for the `file` attribute.

#### Adding a category icon

To add an icon to be used for a category, add a new file to the /icons directory with
the ID of the category as its name, e.g. my_category_id.svg. Then add the
`iconFile` property to the category object in `index.json`.


#### Creating a points category
Categories are generic pool <> metadata associations that are ingested by the API. We use these categories for specific use cases like 3rd party point programs. To add a new point program category there are a couple of things to pay attention to.
1. The `id` should include `points`, preferably as a prepend, e.g. `id: "points_protocol_name"`.
2. If the points program has a multiple, you can use the `value` attribute to specify that multiple. If the multiple is 5x then `value: "5"`.
