Configuring different options for Plex Meta Manager can be done in the Settings. These include enabling a cache to store each Plex GUID and its accompanying IDs to vastly speed up the execution of the script, defining the Image Asset Directory for local assets, setting a global Sync Mode, and many other display features.

A `settings` mapping can be either in the root of the config file as global mapping for all libraries or you can specify the `settings` mapping individually per library. Some settings can be individually set per collection using [Collection Details](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Collection-Details).

Below is a `settings` mapping example and the full set of attributes:
```yaml
settings:
  cache: true
  cache_expiration: 60
  asset_directory: config/assets
  asset_folders: true
  create_asset_folders: false
  sync_mode: append
  collection_minimum: 1
  delete_below_minimum: true
  run_again_delay: 2
  missing_only_released: false
  show_unmanaged: true
  show_filtered: false
  show_missing: true
  show_missing_assets: true
  save_missing: true
  tvdb_language: eng
```

| Name | Attribute | Allowed Values | Global Level | Library Level | Collection Level |
| :--- | :--- | :--- | :---: | :---: | :---: |
| [Cache](#cache) | `cache` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :x: | :x: |
| [Cache Expiration](#cache) | `cache_expiration` | **integer**<br>**default: 60** | :heavy_check_mark: | :x: | :x: |
| [Image Asset Directory](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Image-Asset-Directory) | `asset_directory` | **list of paths**<br>**default: [Directory containing YAML config]/assets** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Image Asset Folders](#image-asset-folders) | `asset_folders` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Create Asset Folders](#create-asset-folders) | `create_asset_folders` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Sync Mode](#sync-mode) | `sync_mode` | `append` or `sync`<br>**default: append** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Collection Minimum](#collection-minimum) | `collection_minimum` | **integer**<br>**default: 1** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Delete Below Minimum](#delete-below-minimum) | `delete_below_minimum` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Run Again Delay](run-again-delay) | `run_again_delay` | **integer**<br>**default: 0** | :heavy_check_mark: | :x: | :x: |
| [Missing Only Released](#missing-only-released) | `missing_only_released` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Show Unmanaged Collections](#show-unmanaged-collections) | `show_unmanaged` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Show Filtered Collections](#show-filtered-collections) | `show_filtered` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Show Missing](#show-missing) | `show_missing` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Show Missing Assets](#show-missing-assets) | `show_missing_assets` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Save Missing](#save-missing) | `save_missing` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [TVDb Language](#tvdb-language) | `tvdb_language` | [ISO 639-2 Language Code](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes) or Blank for original Language<br>**default:**  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

## Cache

Will use a cached database for faster processing. The cache file is created in the same location as your config file.

You can change the number of `cache_expiration` to set the number of days before each cache mapping expires and has to be reloaded

## Image Asset Folders
When searching [Image Asset Directories](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Image-Asset-Directory) search for named folders vs named files<br>i.e. `assets/Star Wars.png` vs `assets/Star Wars/poster.png`.

## Create Asset Folders
When using the `assets_for_all` [Library Operation](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Operations-Attributes) folders will be created for each Item in your library for assets to be placed in.

## Sync Mode
Set the default `sync_mode`. It can be either `append` when you want to add only and `sync` when you want to add and remove from collections.

## Collection Minimum
Minimum number of items that must be found in order to update a collection.

## Delete Below Minimum
When a collection is run it will be deleted if it is below the minimum specified by `collection_minimum`.

## Run Again Delay
Number of minutes to run `run_again` collections after daily run is finished.

A collection is a `run_again` collection if it has the `run_again` [Collection Detail](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Collection-Details#setting-details) attribute set to true.



## Missing Only Released
Library Level toggle to filter missing items from a collection that has yet to be released.

## Show Unmanaged Collections
Show collections not managed by Plex Meta Manager at the end of each run.

## Show Filtered Collections
Library Level toggle to show items filtered from collections.

## Show Missing
Library Level toggle to show items missing from collections

## Show Missing Assets
Library Level toggle to silence missing assets warnings.

## Save Missing
Library Level toggle to save items missing from collections to a filein the same directory as your Metadata file.

## TVDb Language
Use an [ISO 639-2 Language Code](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes) to specify the language to query TVDb in.

If no language is specified or the specified language is not found then the original language is used.
