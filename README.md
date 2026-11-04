# RadioPad registry data

The Registry reads and writes the `data/` namespace. Edit files under `data/accounts/`; the root-level `accounts/` directory is a legacy snapshot and is not read by the current Registry. The two trees are not synchronized.

```text
data/accounts/<account>.json                         Account metadata
data/accounts/<account>/stations.json                Stations keyed by call sign
data/accounts/<account>/radio-dials/<dial>.json       Ordered station references
data/accounts/<account>/players/<player>.json        Player configuration
```

`data/accounts/community/stations.json` defines shared stations. The Casa Briceburg dial is `data/accounts/community/radio-dials/briceburg.json`, identified by `community/briceburg`. Its station list contains qualified keys such as `community/KANW`. Living Room and Cañones both reference this dial from their player records under `data/accounts/briceburg/players/`.

Merge changes to `main` for the deployed Git-backed Registry to read them. With RadioDial watching enabled, the switchboard periodically revalidates active dials and pushes changed revisions to connected players and controllers; compatible players reload their dial without restarting. The remote controller's Control tab follows these updates; its standalone Listen tab requires a refresh. Git fetch and dial-check intervals default to 30 seconds each. Custom deployment settings, disconnected or older clients, and failed requests can delay updates.
