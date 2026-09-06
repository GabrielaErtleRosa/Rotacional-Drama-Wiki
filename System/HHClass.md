---
fields:
  - name: Members
    type: MultiFile
    options:
      dvQueryString: dv.pages('"Sims"')
    path: ""
    id: bAhTjT
  - name: Related to
    type: MultiFile
    options:
      dvQueryString: dv.pages('"HouseHolds"')
    path: ""
    id: p3NYWR
  - name: Original From
    type: File
    options:
      dvQueryString: dv.pages('"Worlds"')
    path: ""
    id: eiYRAq
  - name: Income
    type: Select
    options:
      sourceType: ValuesList
      valuesList:
        "1": Rich
        "2": Poor
        "3": Middle class
    path: ""
    id: KfSqXI
version: "2.4"
limit: 20
mapWithTag: false
icon: package
tagNames:
filesPaths:
bookmarksGroups:
excludes:
extends:
savedViews: []
favoriteView:
fieldsOrder:
  - KfSqXI
  - eiYRAq
  - p3NYWR
  - bAhTjT
---
