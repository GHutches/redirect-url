# redirect-url

## Usage

Links like [`https://ghutches.github.io/redirect-url/index.html?url=sapgui:-command=IW32`](https://ghutches.github.io/redirect-url/index.html?url=https://www.google.com) will open the url in the url search parameter.

For more about the 'sapgui:' protocol: [`https://github.com/GHutches/sapgui-url-protocol`](https://github.com/GHutches/sapgui-url-protocol)


## Usage in sharepoint lists

The reason I created this site is a workaround to inflexible sharepoint APIs / security. In sharepoint you can add format JSON to fields, to format data in a different way. I wanted to add a button to a field which would enable the user to be able to open url protocol links. Unfortunately this cannot be done with the sharepoint site alone, so the work around is to use a seperate helper site.

This will add a link icon and a link such that when you click on the field, the user will open the link:
```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "a",
  "attributes": {
    "iconName": "Link",
    "target": "_blank",
    "class": "ms-borderColor-white ms-borderColor-themePrimary--hover",
    "href": "='https://ghutches.github.io/copy-to-clipboard/index.html?url=' + @currentField"
  },
  "style": {
    "color": "#272727",
    "text-decoration": "none",
    "font-size": "14px",
    "border-bottom-width": "1px",
    "border-bottom-style": "solid",
    "min-width": "400px"
  },
  "children": [
    {
      "elmType": "span",
      "txtContent": "@currentField",
      "style": {
        "padding-left": "5px"
      }
    }
  ]
}
```