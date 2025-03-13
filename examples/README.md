# Line Item Properties for Shopify Dawn Theme

This feature allows customers to add customization options to products when adding them to the cart. These customization options are stored as line item properties in the cart and can be used for various purposes such as:

- Engraving text
- Gift messages
- Size selections
- Gift wrapping options
- Personalization options
- Custom instructions

## How to Set Up Line Item Properties

### 1. Enable the Feature in Theme Settings

1. Go to your Shopify admin
2. Navigate to Online Store > Themes
3. Click "Customize" on your Dawn theme
4. Select a product page
5. Find the "Buy buttons" block in the sidebar
6. Make sure "Show line item properties" is checked

### 2. Add Metafields to Products

To add line item properties to a specific product, you need to add a metafield to that product with the following structure:

- Namespace: `custom`
- Key: `line_item_properties`
- Type: `json`

The value should be a JSON array of property objects, each with the following structure:

```json
[
  {
    "key": "property_key",
    "label": "Display Label",
    "type": "text|textarea|select|checkbox",
    "required": true|false,
    "default_value": "default value"
  }
]
```

For select type properties, you also need to include an `options` array:

```json
{
  "key": "size",
  "label": "Size",
  "type": "select",
  "required": true,
  "options": [
    {
      "value": "small",
      "label": "Small"
    },
    {
      "value": "medium",
      "label": "Medium"
    },
    {
      "value": "large",
      "label": "Large"
    }
  ],
  "default_value": "medium"
}
```

### 3. Sample Metafield JSON

See the `line_item_properties_metafield.json` file in this directory for a complete example.

## Supported Property Types

- `text`: Single line text input
- `textarea`: Multi-line text input
- `select`: Dropdown selection
- `checkbox`: Checkbox option

## Accessing Line Item Properties in the Cart

Line item properties will be displayed in the cart and checkout pages. They will also be included in order details and notifications.

## Customizing the Appearance

The appearance of line item properties can be customized by modifying the CSS in `assets/section-main-product.css`. 