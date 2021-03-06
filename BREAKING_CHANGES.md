# Breaking Changes

## 2.0 - incomplete list

- Everything in Dynamoose are now classes. This includes `Model` and `Schema`. This means to initalize a new instance of one of these items, you must use the `new` keyword before it
- `scan.count()` has been removed, and `scan.counts()` has been renamed to `scan.count()`.
- Schema `default` value does not pass the model instance into `default` functions any more.
- `Model.update`
	- `$LISTAPPEND` has been removed, and `$ADD` now includes the behavior of `$LISTAPPEND`
	- `$DELETE` now maps to the correct underlying DynamoDB method instead of the previous behavior of mapping to `$REMOVE`
- `dynamoose.model` has been renamed to `dynamoose.Model`
- `dynamoose.local` has been renamed to `dynamoose.aws.ddb.local`
- `Model.getTableReq` has been renamed to `Model.table.create.request`
- `Model.table.create.request` (formerly `Model.getTableReq`) is now an async function
- `model.originalItem` has been renamed to `model.original` (or `Document.original`)
- `Document.original` formerly (`model.originalItem`) no longer returns the last item saved, but the item first retrieved from DynamoDB
- `expires` has been moved from the Schema settings to the Model settings
- `expires.ttl` is now milliseconds as opposed to seconds
- `expires.defaultExpires` is no longer an option (most behavior from this option can be replicated by using the new `dynamoose.undefined` feature)
- `expires.returnExpiredItems` has been renamed to `expires.items.returnExpired`
- `Model.transaction.conditionCheck` has been renamed to `Model.transaction.condition`
- `Model.transaction.condition` options parameter now gets appended to the object returned. This means you can no longer use the helpers that Dynamoose provided to make conditions. Instead, pass in the DynamoDB API level conditions you wish to use
