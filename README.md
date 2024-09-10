# Balancer Metadata

Public metadata for the Balancer protocol.

## Categories
Categories are used to tag sets of pools in the Balancer API and frontend.

### Adding new categories
To add a new category, update the categories json with an object using the following schema:
```ts
  {
    id: string // If it's a points category, prepend id with `points_`, see existing categories for examples.
    name: string
    description: string
    value?: string // Arbitrary value that may be used by the frontend to provider more context, like points multiples for points categories.
    url?: string
    file: string // The file that includes the list of pool IDs that should be associated with this category. Should be a relative path, see existing categories for examples.
    fileIcon?: string // Icon to be used in frontend to represent the category. Should be a relative path, see existing categories for examples.
  }
```
