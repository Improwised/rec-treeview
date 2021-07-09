# Recursive Component Example

This directory is a brief example of a Recursive Component that has be deployed with Vercel.

## Demo

_Live Example: https://rec-treeview-g39cz5bjm-rajbhojani77.vercel.app/_

### How We Created This Example

To get started with Example, you can use the [Create-Nuxt-App CLI](https://www.npmjs.com/package/create-nuxt-app) to initialize the project:

Overall, it's a pretty short exercise into creating a recursive component.

we have used [bootstrap-vue](https://bootstrap-vue.org/docs/components/navbar) to create collapsing container.

First create a component then use in page like given.json data of recipes is also given below.
here you have to define every paths of json.

index.vue
```bash
    <recursive-tab
      v-for="recipe in recipes"
      :name="recipe.name"
      :data="recipe"
      :key="recipe.name"
      :paths="['parent', 'children', 'grandchildren']"
    />
```

Now in component wee have to define component in component. here chage is we have to pop one path in every single recursion
and also we have to check that path is last one or not.

RecursiveTab.vue
```bash
    <recursive-tab
        v-for="child in children"
        :name="child.name"
        :data="child"
        :key="child.name"
        :paths="childPaths"
    />
```

data.json
```bash 
{
  "recipes": [
    {
      "name": "Vegetarian Recipes",
      "parent": [
        {
          "name": "Fruits",
          "children": [
            {
              "name": "Dry Fruits",
              "grandchildren": [
                {
                  "name": "Almond"
                },
                {
                  "name": "Apricot"
                },
                {
                  "name": "Cashewnuts"
                },
                {
                  "name": "Dates"
                },
                {
                  "name": "Walnuts"
                },
                {
                  "name": "Peanuts"
                },
                {
                  "name": "Pistachios"
                }
              ]
            },
            {
              "name": "Fresh Fruits",
              "grandchildren": [
                {
                  "name": "Apple"
                },
                {
                  "name": "Banana"
                },
                {
                  "name": "Orange"
                },
                {
                  "name": "Mango"
                },
                {
                  "name": "Grapes"
                }
              ]
            }
          ]
        },
        {
          "name": "Soup",
          "children": [
            {
              "name": "Tomato Soup"
            },
            {
              "name": "Loaded Potato Soup"
            },
            {
              "name": "French Onion Soup"
            }
          ]
        }
      ]
    }
  ]
}

```

## Build Setup

```bash
# install dependencies
npm install

# dev server with hot reload
npm run dev

# build for production
npm build
```
