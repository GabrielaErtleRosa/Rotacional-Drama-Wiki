---
profile: BellaGoth.png
Core Aspiration: Fitness
Aspiration:
Traits:
Career:
Life Stage:
HouseHold:
Parents:
Partner:
Born Roud:
fileClass: CharacterClass
adopted: false
Deceased: false
Children:
Natural From:
Current Living:
Sibling (s):
Step Sibling (s):
Friends:
Ex (s):
banner: Assets/Banners/7107311908726535 1.jpg
banner-fade: 100
banner-height: 360
icon-image: https://i.pinimg.com/1200x/b7/5b/29/b75b29441bbd967deda4365441497221.jpg
banner-icon-image-alignment: left
icon-x: 6
icon-size: 105
icon-y: 100
icon-image-size-multiplier: 1.8
---

```dataviewjs
const char = dv.current();
const img = char.profile;

if(img){

const path = "Assets/Profiles/" + img;
const url = app.vault.adapter.getResourcePath(path);

dv.paragraph(`
<div class="character-profile-wrapper">

<img src="${url}" class="character-profile-image">

</div>
`);
}
```





# Biography

# Relationships

# Goals

# Events
```