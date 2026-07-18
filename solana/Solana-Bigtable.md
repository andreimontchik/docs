# Links
* [The repo](https://github.com/solana-labs/solana-bigtable)

# Access 
## Google
* Docs
  * [Google Service Account Overview](https://cloud.google.com/iam/docs/service-account-overview)
  * [How to create service account keys](https://cloud.google.com/iam/docs/keys-create-delete)

* WIP
  1. Create Google Workspace for an organization, I am using the existing `montchik.net` one.
  1. Enable the `Google Cloud Platform` for the organization: `Admin Console -> Additional Google Services -> Google Cloud Platform -> On`
  1. Set up Google Cloud for the Google organization. Partially configured it for the `montchik.net` organization.
  1. Create new Google Project for the organization. I created the `Research` project under the `montchik.net` organization.

## Solana
* Create Service account
  * Mainnet: https://console.cloud.google.com/iam-admin/serviceaccounts?project=mainnet-beta
  * Devnet: https://console.cloud.google.com/iam-admin/serviceaccounts?project=principal-lane-200702

# The Solana Bigtable Contents
* The bigtable folders contain an information for single epoch, where full snapshot is taken at the end of prior epoch slot and the rocksdb is archived at the beginning of the next epoch.
* There is also the `hourly` snapshots directory containing incremental hourly snapshots.
* [Example](https://console.cloud.google.com/storage/browser/mainnet-beta-ledger-us-ny5/253146413;tab=objects?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&project=mainnet-beta&prefix=&forceOnObjectsSortingFiltering=false)
  * bounds.txt
    ```
    Ledger has data for 431379 slots 253146413 to 253584122
    with 424579 rooted slots from 253146413 to 253584089
    and 33 slots past the last root
    ```
  * epoch.txt
    ```
    586
    ```
  * `rocksdb.tar.zst` size is 756.1 GB
  * `snapshot-253146413-FHAUKUxEuP1teP8cHu3axW1HT4t9Wu2T9SNZYXJgbV58.tar.zst` size is 59.4 GB
# How To
## Access the Solana Bigtable Bucket
   Open on of the the following URLs in browser.
   * New York: [mainnet-beta-ledger-us-ny5](https://console.cloud.google.com/storage/browser/mainnet-beta-ledger-us-ny5)
   * Frankfurt: [mainnet-beta-ledger-europe-fr2](https://console.cloud.google.com/storage/browser/mainnet-beta-ledger-europe-fr2)
   * Singapore: [mainnet-beta-ledger-asia-sg1](https://console.cloud.google.com/storage/browser/mainnet-beta-ledger-asia-sg1)
## [Ledger How To](Solana-Validator-Ledger.md#how-to)