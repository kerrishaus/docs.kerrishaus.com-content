# Using Search boxes on the Portal
Most Search boxes on the Portal are standardised, so this advice should apply everywhere.

The default behaviour of the search box is to split the entire search query into individual words (by spaces) and return any results which contains those words anywhere in the container.

By enclosing a search query in quotation marks, that query will not be broken into individual words. For example, a search for `red and blue` might return "red", "and", "blue", or any combination thereof. However, a search for `"red and blue"` will only return results which contain "red and blue" exactly. If there are other search terms around a quoted group, the quoted group and other terms will be separated and quered individually. For example, a query for `red "and blue"` could return results with either "red" or "and blue", or both.
