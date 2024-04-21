# stickers.setStickerSetThumb
Set stickerset thumbnail

```
messages.stickerSet#6e153f16 set:StickerSet packs:Vector<StickerPack> keywords:Vector<StickerKeyword> documents:Vector<Document> = messages.StickerSet;
messages.stickerSetNotModified#d3f924eb = messages.StickerSet;
---functions---
stickers.setStickerSetThumb#a76a5392 flags:# stickerset:InputStickerSet thumb:flags.0?InputDocument thumb_document_id:flags.1?long = messages.StickerSet;
```

## Parameters
| Name | Type | Description |
| ---- | :----: | ----------- |
| flags | # | Flags, see TL conditional fields |
| stickerset | InputStickerSet | Stickerset |
| thumb | flags.0?InputDocument | Thumbnail (only for normal stickersets, not custom emoji stickersets). |
| thumb_document_id | flags.1?long | Only for custom emoji stickersets, ID of a custom emoji present in the set to use as thumbnail; pass 0 to fallback to the first custom emoji of the set. |


## Result
messages.StickerSet

## Possible errors
| Code | Type | Description |
| ---- | :----: | ----------- |
| 400 | STICKERSET_INVALID | The provided sticker set is invalid. |
| 400 | STICKER_THUMB_PNG_NOPNG | Incorrect stickerset thumb file provided, PNG / WEBP expected. |
| 400 | STICKER_THUMB_TGS_NOTGS | Incorrect stickerset TGS thumb file provided. |

