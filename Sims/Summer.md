---
Gender: Female
Generation:
Born Round: "[[Round 2]]"
Natural From: "[[Worlds/Sem título]]"
Current Living: "[[Worlds/Sem título]]"
Life Stage: Baby
Career:
  - Secret Agent
  - Cook
Core Aspiration: Comida
Aspiration: Rei/Rainha das Travessuras
Traits:
  - "Pateta "
  - "Glutão "
  - "Romântico "
Sexuality:
  - Bissexual
Partner: "[[J Huntington]]"
fileClass: CharacterClass
Children:
Friends:
  - "[[Gina Goth]]"
Ex (s):
  - "[[J Huntington]]"
  - "[[Kurt Pancakes]]"
  - "[[Helena Landgraab]]"
  - "[[Gina Goth]]"
  - "[[Don Lothario]]"
  - "[[Bella Goth]]"
Adopted: true
Deceased: true
Epitaph:
HouseHold: "[[HouseHolds/Sem título]]"
Step Sibling (s):
  - "[[Don Lothario]]"
  - "[[Bella Goth]]"
Sibling (s):
  - "[[Travis]]"
Parents:
  - "[[Bella Goth]]"
Adoptive Parents:
  - "[[Helena Landgraab]]"
  - "[[Travis]]"
cssclasses:
  - sim-template
Death Round: "[[Round 2]]"
Death By: Drowning
gallery: []
---


> [!picture]
> ![[AvatarDefault.png]]


> [!Sim Info]
> ```dataviewjs
> const file = app.workspace.getActiveFile();
> const char = dv.page(file?.path);
>
> if (!char) {
>     dv.paragraph("⏳ carregando...");
> } else {
>     dv.table(
>         ["Family Info", " "],
>         [
>             ["Household", char["HouseHold"] ?? "None"],
>             ["Parents", char["Parents"] ?? "None"],
>
>             ...(char["Adopted"]
>                 ? [["Adoptive Parents", char["Adoptive Parents"] ?? "None"]]
>                 : []),
>
>             ["Sibling (s)", char["Sibling (s)"] ?? "None"],
>             ["Step Sibling (s)", char["Step Sibling (s)"] ?? "None"]
>         ]
>     );
> }
> ```

 

> [!sidebar-right]  
>  
> ```dataviewjs  
> 
> const file = app.workspace.getActiveFile();  
> const char = dv.page(file?.path);  
> 
> dv.container.classList.remove("death-info");
> 
> if (!char) {  
> dv.paragraph("⏳ carregando...");  
> } else if (char["Deceased"]) {  
> dv.container.classList.add("death-info");  
>  
> dv.table(  
> ["💀 Deceased Sim ✞ ", " "],  
> [  
> ["Death By", char["Death By"] ?? "None"],  
>  
> [  
> "Death Round",  
> char["Death Round"]  
> ? dv.fileLink(char["Death Round"].path)  
> : "None"  
> ],  
>  
> ["Epitaph", char["Epitaph"] ?? "None"]  
> ]  
> );  
> }  
> ```
>
>> [!Biography]
> >Uma biografiaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
> >scrr o
> >aa
>>
> >yee
>
>
>> [!about]
>> - Loves fishing
>> - LALA
>> -  Afraid of ghosts
>> - Favorite color: blue
>> - Always carries a notebook
>
>> [!Goals]  
>>   - revenge
>>   - omg
>>   - ev
>>   
>>   
>>
>>
>>
>>
>
>
>









```dataviewjs
const file = app.workspace.getActiveFile();
const char = dv.page(file?.path);

if (!char) {
    dv.paragraph("⏳ carregando...");
} else {
    const simPath = char.file.path;

    const events = dv.pages('"Events"')
        .where(e => e.Participants?.some(p => p?.path === simPath));

    const gallery = dv.container.createDiv({ cls: "round-gallery" });

    for (const event of events) {
	
        const card = gallery.createDiv({ cls: "event-card" });

        // imagem
        if (event.cover) {
    const imgFile = app.metadataCache.getFirstLinkpathDest(
        event.cover?.path ?? event.cover,
        event.file.path
    );
    if (imgFile) {
        const src = app.vault.getResourcePath(imgFile);
        card.createEl("img", { attr: { src } });
    
            }
        }

        // título clicável
        const title = card.createEl("p", {
            text: event.file.name,
            cls: "event-title"
        });
        title.addEventListener("click", (e) => {
            e.preventDefault();
            app.workspace.openLinkText(event.file.name, event.file.path, false);
        });
        title.style.cursor = "pointer";

        // descrição
        if (event.Description) {
            card.createEl("p", {
                text: event.Description,
                cls: "event-description"
            });
        }

        // participantes
        if (event.Participants) {
            const names = event.Participants
                .map(p => p?.path?.split("/").pop()?.replace(".md", "") ?? "?")
                .join(", ");
            const part = card.createEl("p", {});
            part.createEl("strong", { text: "Participants: " });
            part.createSpan({ text: names });
        }
    }
}
```

