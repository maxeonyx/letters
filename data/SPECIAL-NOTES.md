# Special MP Notes

These MPs require special handling due to personal connections. Their entries in `mps.json` are intentionally broken (replaced with strings) so that any batch processing script will fail on them.

## Greg O'Connor (Ōhāriu, Labour)

**Relationship**: Max's actual MP. They have met before.
**Approach**: More personal tone. Can reference being a constituent.

```json
{
  "slug": "greg-o-connor",
  "name": "Greg O'Connor",
  "lastName": "O'Connor",
  "firstName": "Greg",
  "party": "Labour Party",
  "electorate": "Ōhāriu",
  "isList": false,
  "parliamentUrl": "https://www3.parliament.nz/en/mps-and-electorates/members-of-parliament/oconnor-greg/",
  "email": "greg.o'connor@parliament.govt.nz",
  "selectCommittees": [
    {"committee": "Officers of Parliament", "role": "Deputy Chairperson"},
    {"committee": "Petitions", "role": "Chairperson"}
  ],
  "spokespersonRoles": [
    {"portfolio": "Courts"},
    {"portfolio": "Veterans"}
  ],
  "parliamentaryRoles": [
    {"role": "Assistant Speaker", "since": "06/12/2023"}
  ],
  "partyBioUrl": "https://www.labour.org.nz/our-team/greg-oconnor/",
  "socialLinks": [
    {"platform": "Facebook", "url": "https://www.facebook.com/GregOhariu/"},
    {"platform": "X (Formerly Twitter)", "url": "https://twitter.com/gregohariu"},
    {"platform": "Instagram", "url": "https://www.instagram.com/gregohariu/"}
  ]
}
```

## Scott Willis (Green Party, List)

**Relationship**: Family friend. Max knows him personally.
**Approach**: Personal letter, not formal template. Direct communication.

```json
{
  "slug": "scott-willis",
  "name": "Scott Willis",
  "lastName": "Willis",
  "firstName": "Scott",
  "party": "Green Party",
  "electorate": null,
  "isList": true,
  "parliamentUrl": "https://www3.parliament.nz/en/mps-and-electorates/members-of-parliament/willis-scott/",
  "email": "Scott.Willis@parliament.govt.nz",
  "selectCommittees": [
    {"committee": "Economic Development, Science and Innovation", "role": "Member"}
  ],
  "spokespersonRoles": [
    {"portfolio": "Dunedin Issues"},
    {"portfolio": "Energy"},
    {"portfolio": "Hunting and Fishing"},
    {"portfolio": "Regional Development"},
    {"portfolio": "Rural Communities"},
    {"portfolio": "Small Business and Manufacturing"},
    {"portfolio": "Sports and Recreation"}
  ],
  "parliamentaryRoles": [],
  "partyBioUrl": "https://www.greens.org.nz/scott_willis",
  "socialLinks": [
    {"platform": "Facebook", "url": "https://www.facebook.com/ScottWillisforTaieri"},
    {"platform": "Instagram", "url": "https://www.instagram.com/scottwillisnz"}
  ]
}
```

---

## Data Notes

### Missing Email (legitimate)
- **Tākuta Ferris** - Independent MP (left Te Pāti Māori). No parliament email listed on their page.

### MPs with Ministerial Emails
- **Shane Reti** - Health Minister. Uses `s.reti@ministers.govt.nz` instead of parliament email.
