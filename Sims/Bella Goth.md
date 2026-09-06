---
HouseHold:
Generation:
Life Stage:
Natural From:
Current Living:
Core Aspiration:
Aspiration:
Traits:
Career:
Partner:
Children:
Parents:
fileClass: CharacterClass
adopted: false
Deceased: false
Sibling (s):
Step Sibling (s):
Friends:
Ex (s):
Epitaph:
Adoptive Parents:
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
> [!picture]
> ![[BellaGoth.png]]



#Family/Goth 

# Biography

# Relationships

# Goals

# Events
```