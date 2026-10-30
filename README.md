# EnforcementVessels

A list of vessels used in immigration enforcement at sea by the United States. Each vessel carries its MMSI, the number it broadcasts on AIS, and the entry that put it on the list. Each entry carries its evidence and sources.

This is a downloadable file, not an API.

## Download

Release `data`, replaced on every build:

* `enforcementvessels.json`: the list
* `SHA256SUMS`: its checksum

`https://github.com/StrausbergAutomationWorks/EnforcementVessels/releases/download/data/enforcementvessels.json`

## What is on the list

US Coast Guard cutters that the Coast Guard's own releases, photos or stories name in migrant interdiction since 2025-01-20: interdicting, repatriating, transferring or rescuing people at sea, or on a counter-migration or maritime border security patrol. Each evidence item says which of those two it is (`direct` or `patrol`) and links the source.

Status is one of:

* `sourced`: published evidence names the vessel in the work described.
* `cleared`: found not to be involved. Cleared entries stay in the file with the reason and the source.

**Entries are only ever added.** One leaves the active list only when it is found not to be involved, and it stays in the file as `cleared`.

## Where a listed vessel counts

Every listed cutter also does other work. **A listed vessel counts as doing immigration enforcement only while it is inside one of these theatres**, drawn around the places named in the cited releases. Elsewhere it is an ordinary Coast Guard vessel. The boxes are in the file's `theatres` field, as `[south, west, north, east]` in degrees.

| Theatre | Latitude | Longitude |
|---|---|---|
| Mona Passage and Puerto Rico | 17.5 to 19.5 N | 69.5 to 65.0 W |
| Windward Passage | 19.5 to 23.0 N | 75.5 to 70.5 W |
| Florida Straits, the Bahamas and the Yucatan Channel | 21.5 to 27.5 N | 87.0 to 76.5 W |
| Southern California | 32.3 to 34.5 N | 121.5 to 117.0 W |

## What the list cannot tell you

* **Being on the list says nothing about what a vessel is doing now.** Every listed cutter also does search and rescue, counter-drug patrols, fisheries enforcement and other work.
* **It only lists what is published.** A vessel the Coast Guard has not named in a release is not on it. Absence from the list is not evidence of anything.
* **Small boats and river patrols are mostly absent.** Releases rarely name them, and many do not broadcast on AIS.
* **An MMSI is matched by the name the vessel broadcast in US waters** (Marine Cadastre, 2025). A vessel never heard there is kept in `entries.json` with no MMSI and left out of `vessels`, since it cannot be matched on AIS.

## Format

```json
{
 "name": "EnforcementVessels",
 "schema": 1,
 "built": "2026-10-30T00:00:00Z",
 "license": "ODbL-1.0",
 "attribution": "...",
 "theatres": [{"id": "mona", "name": "Mona Passage and Puerto Rico", "box": [17.5, -69.5, 19.5, -65.0]}],
 "counts": {"vessels": 41, "entries": 41, "held_back_no_mmsi": 1, "by_status": {"sourced": 41}},
 "entries": [{"id": "uscg-active", "kind": "vessel", "name": "USCGC Active (WMEC 618)", "short": "USCG", "agency": "US Coast Guard", "mmsi": ["367269000"], "mmsi_basis": "...", "hull": "WMEC 618", "status": "sourced", "evidence": [{"date": "2025-06-15", "kind": "direct", "what": "...", "source_url": "..."}], "added": "2026-10-30", "cleared": null}],
 "vessels": [{"mmsi": "367269000", "name": "USCGC Active (WMEC 618)", "agency": "US Coast Guard", "hull": "WMEC 618", "entry": "uscg-active", "status": "sourced"}]
}
```

An MMSI is nine digits, as a string. A vessel heard under two MMSIs appears once per MMSI in `vessels`.

## Sources and licence

* Evidence: US Coast Guard releases, photos and stories, from the Coast Guard newsroom, its email bulletins and DVIDS (Defense Visual Information Distribution Service). US government works.
* MMSIs: Marine Cadastre AIS vessel traffic data (NOAA Office for Coastal Management and the US Coast Guard), public domain.
* The data is licensed under the Open Database License (ODbL) 1.0. See `DATA_LICENSE.md`.

Not affiliated with or endorsed by any government agency.

Corrections, with a source, are welcome as an issue.
