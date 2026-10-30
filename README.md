# GolfCard Live
Public viewer for GolfCard live scoreboards: `https://mridgway-lab.github.io/golfcard-live/?r=<roundID>`.
Reads record `live-<roundID>` (type LiveBoard, field `payload` JSON) from the CloudKit public DB of `iCloud.com.dtrt.golfcard` using a read-only API token.

curl:
    curl -s -X POST "https://api.apple-cloudkit.com/database/1/iCloud.com.dtrt.golfcard/production/public/records/lookup?ckAPIToken=TOKEN" \
      -H 'Content-Type: application/json' -d '{"records":[{"recordName":"live-<roundid lowercase>"}]}' | jq -r '.records[0].fields.payload.value' | jq
