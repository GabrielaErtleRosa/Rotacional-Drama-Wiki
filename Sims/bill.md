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
Children: ["[[Kurt Pancakes]]"]
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
HouseHold: "[[BFF]]"
Step Sibling (s):
  - "[[Travis Scott]]"
  - "[[Don Lothario]]"
  - "[[Regina]]"
  - "[[J Huntington]]"
  - "[[Helena Landgraab]]"
  - "[[Gina Goth]]"
  - "[[Kurt Pancakes]]"
  - "[[Jhonny]]"
  - "[[Summer]]"
Sibling (s):
  - "[[Bella Goth]]"
  - "[[Bailey Richards]]"
  - "[[Kurt Pancakes]]"
  - "[[Summer]]"
  - "[[Travis Scott]]"
  - "[[Regina]]"
  - "[[Helena Landgraab]]"
  - "[[Gina Goth]]"
  - "[[Don Lothario]]"
  - "[[Jhonny]]"
Parents:
  - "[[Bella Goth]]"
  - "[[J Huntington]]"
Adoptive Parents:
  - "[[lol]]"
  - "[[Regina]]"
cssclasses:
  - sim-template
Death Round: "[[Round 2]]"
Death By: Drowning
gallery: []
picture: "[[BellaGoth.png]]"
---






> [!sidebar-left]
>> [!picture]
>> ```dataviewjs
>> const file = app.workspace.getActiveFile();
>> const char = dv.page(file?.path);
>> dv.container.empty();
>>
>> if (!char?.picture) {
>>     dv.paragraph("Sem foto");
>> } else {
>>     const imgFile = app.metadataCache.getFirstLinkpathDest(
>>         char.picture?.path ?? char.picture,
>>         file.path
>>     );
>>     if (imgFile) {
>>         const src = app.vault.getResourcePath(imgFile);
>>         dv.container.createEl("img", { attr: { src } });
>>     }
>> }
>> ```
> > 
> > 
>
> > [!Sim Info]
> >
> > ```dataviewjs
> > const file = app.workspace.getActiveFile();
> > const char = dv.page(file?.path);
> > dv.container.empty();
> > if (!char) {
> >     dv.paragraph("⏳ carregando...");
> > } else {
> >     dv.container.classList.add("sim-info-tables");
> >
> >     // family info
> >     dv.table(
> >         ["Family Info", " "],
> >         [
> >             
> >             ["Parents", char["Parents"] ?? "None"],
> >
> >             ...(char["Adopted"]
> >                 ? [["Adoptive Parents", char["Adoptive Parents"] ?? "None"]]
> >                 : []),
> >
> >             ["Sibling (s)", char["Sibling (s)"] ?? "None"],
> >             ...(char["Step Sibling (s)"] ? [["Step Sibling (s)", char["Step Sibling (s)"]]] : []),
> >         ]
> >     );
> >     const familyThs = dv.container.querySelectorAll("th");
> > 	const secondTh = familyThs[1];
> >     if (secondTh && !secondTh.querySelector(".family-info-icon")) {
> > 	    const iconEl = document.createElement("span");
> > 	    iconEl.className = "family-info-icon";
> > 	    obsidian.setIcon(iconEl, "users-round");
> > 	    secondTh.append(iconEl); }
> >
> >     // household info
> >     const householdLink = char["HouseHold"];
> >     if (householdLink) {
> >         const household = dv.page(householdLink.path ?? householdLink);
> >         const income = char?.income
> >             ?? household?.income
> >             ?? household?.INCOME
> >             ?? "None";
> >
> >         dv.table(
> >             ["Household Info", " "],
> >             [
> >                 ["Household", dv.fileLink(householdLink.path)],
> >                 ["Income", income]
> >             ]
> >         );
> >
> >         const ths = dv.container.querySelectorAll("th");
> >         const lastTh = ths[ths.length - 1];
> >         if (lastTh && !lastTh.querySelector(".household-info-icon")) {
> >             const iconEl = document.createElement("span");
> >             iconEl.className = "household-info-icon";
> >             obsidian.setIcon(iconEl, "house");
> >             lastTh.prepend(iconEl);
> >         }
> >     }
> > }
> > ```
> >
> >
> >
 ```dataviewjs

 const file = app.workspace.getActiveFile();
 const char = dv.page(file?.path);
 dv.container.empty();
 if (!char) {
     dv.paragraph("⏳ carregando...");
 } else {
     const families = (char.file.tags ?? [])
         .filter(t => t.toLowerCase().startsWith("#family/"))
         .map(t => t.replace(/#family\//i, "")
             .replace(/-/g, " ")
             .replace(/\b\w/g, l => l.toUpperCase())
         );

     if (families.length > 0) {
         dv.container.classList.add("family-tree-block");

         const titleEl = dv.container.createEl("div", { cls: "family-tree-title" });
         const iconEl = titleEl.createEl("span");
         obsidian.setIcon(iconEl, "git-branch");
         titleEl.createEl("span", { text: "Family Lines" });

         const tagList = dv.container.createEl("div", { cls: "family-tag-list" });
         for (const family of families) {
             tagList.createEl("span", { text: family, cls: "family-tag-pill" });
         }
     }
 }
 

 ```





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
>
>>[!Sim-Gallery]
>>```dataviewjs
>>
>> const file = app.workspace.getActiveFile();
>> const char = dv.page(file?.path);
>> dv.container.empty();
>> if (!char) {
>>     dv.paragraph("⏳ carregando...");
>> } else {
>>     const container = dv.container.createDiv({ cls: "sim-photo-gallery" });
>> 
>>     const addBtn = container.createEl("button", {
>>         text: "+ Add photo",
>>         cls: "gallery-add-btn"
>>     });
>> 
>>     addBtn.addEventListener("click", () => {
>>         const input = document.createElement("input");
>>         input.type = "file";
>>         input.accept = "image/*";
>> 
>>         input.addEventListener("change", async () => {
>>             const file2 = input.files[0];
>>             if (!file2) return;
>> 
>>             const buffer = await file2.arrayBuffer();
>>             const destPath = `Assets/General-gallery/${file2.name}`;
>>             const existing = app.vault.getAbstractFileByPath(destPath);
>>             if (!existing) {
>>                 await app.vault.createFolder("Assets/General-gallery").catch(() => {});
>>                 await app.vault.createBinary(destPath, buffer);
>>             }
>> 
>>             await app.fileManager.processFrontMatter(file, fm => {
>>                 if (!fm.gallery) fm.gallery = [];
>>                 if (!fm.gallery.includes(file2.name)) fm.gallery.push(file2.name);
>>             });
>>         });
>> 
>>         input.click();
>>     });
>> 
>>     const overlay = document.createElement("div");
>>     overlay.className = "gallery-fullscreen-overlay";
>> 
>>     const fullImg = document.createElement("img");
>>     fullImg.className = "gallery-fullscreen-img";
>> 
>>     const closeBtn = document.createElement("button");
>>     closeBtn.className = "gallery-fullscreen-close";
>>     closeBtn.textContent = "✕";
>> 
>>     overlay.appendChild(fullImg);
>>     overlay.appendChild(closeBtn);
>> 
>>     closeBtn.onclick = () => overlay.remove();
>>     overlay.onclick = (e) => { if (e.target === overlay) overlay.remove(); };
>> 
>>     const photos = char.gallery ?? [];
>> 
>> 
>>     const grid = container.createDiv({ cls: "sim-photo-grid" });
>>     let dragSrc = null;
>> 
>>     const renderCards = (photoList) => {
>>         grid.empty();
>> 
>>         for (const photo of photoList) {
>>             const imgFile = app.metadataCache.getFirstLinkpathDest(photo, file.path);
>>             if (!imgFile) continue;
>> 
>>             const src = app.vault.getResourcePath(imgFile);
>>             const card = grid.createDiv({ cls: "sim-photo-card", attr: { draggable: "true" } 
>>             });
>> 
>>             const img = card.createEl("img", { attr: { src } });
>> 
>>             img.addEventListener("click", () => {
>>                 fullImg.src = src;
>>                 document.body.appendChild(overlay);
>>             });
>> 
>>             const del = card.createEl("button", { text: "✕", cls: "photo-delete-btn" });
>>             del.addEventListener("click", async (e) => {
>>                 e.stopPropagation();
>>                 await app.fileManager.processFrontMatter(file, fm => {
>>                     fm.gallery = (fm.gallery ?? []).filter(p => p !== photo);
>>                 });
>>                 card.remove();
>>             });
>> 
>>             card.addEventListener("dragstart", () => {
>>                 dragSrc = photo;
>>                 card.classList.add("dragging");
>>             });
>> 
>>             card.addEventListener("dragend", () => {
>>                 card.classList.remove("dragging");
>>                 document.querySelectorAll(".sim-photo-card").forEach(c => 
>>                 c.classList.remove("drag-over"));
>>             });
>> 
>>             card.addEventListener("dragover", (e) => {
>>                 e.preventDefault();
>>                 card.classList.add("drag-over");
>>             });
>> 
>>             card.addEventListener("dragleave", () => {
>>                 card.classList.remove("drag-over");
>>             });
>> 
>>             card.addEventListener("drop", async (e) => {
>>                 e.preventDefault();
>>                 card.classList.remove("drag-over");
>>                 if (dragSrc === photo) return;
>> 
>>                 await app.fileManager.processFrontMatter(file, fm => {
>>                     const list = [...(fm.gallery ?? [])];
>>                     const fromIdx = list.indexOf(dragSrc);
>>                     const toIdx = list.indexOf(photo);
>>                     list.splice(fromIdx, 1);
>>                     list.splice(toIdx, 0, dragSrc);
>>                     fm.gallery = list;
>>                 });
>> 
>>                 const updated = dv.page(file.path)?.gallery ?? [];
>>                 renderCards(updated);
>>             });
>>         }
>>     };
>> 
>>     renderCards(photos);
>> }
>> 
>>```
>>
>>
>>>> [!related-sims] Related Sims
>> ```dataviewjs
>> const file = app.workspace.getActiveFile();
>> const char = dv.page(file?.path);
>> dv.container.empty();
>> if (!char) {
>>     dv.paragraph("⏳ carregando...");
>> } else {
>>     const myFamilies = new Set(
>>         (char.file.tags ?? [])
>>             .filter(t => t.toLowerCase().startsWith("#family/"))
>>             .map(t => t.toLowerCase())
>>     );
>> 
>>     if (myFamilies.size > 0) {
>>         const related = dv.pages('"Sims"')
>>             .where(s =>
>>                 s.file.path !== char.file.path &&
>>                 (s.file.tags ?? []).some(t => myFamilies.has(t.toLowerCase()))
>>             );
>> 
>>         if (related.length > 0) {
>>             const grid = dv.container.createDiv({ cls: "related-sims-grid" });
>> 
>>             for (const sim of related) {
>>                 const card = grid.createDiv({ cls: "related-sim-card" });
>> 
>>                 card.style.cursor = "pointer";
>>                 card.addEventListener("click", () => {
>>                     app.workspace.openLinkText(sim.file.name, sim.file.path, false);
>>                 });
>> 
>>                 if (sim.picture) {
>>                     const imgFile = app.metadataCache.getFirstLinkpathDest(
>>                         sim.picture?.path ?? sim.picture,
>>                         sim.file.path
>>                     );
>>                     if (imgFile) {
>>                         const src = app.vault.getResourcePath(imgFile);
>>                         card.createEl("img", { attr: { src } });
>>                     }
>>                 } else {
>>                     card.createDiv({ cls: "related-sim-no-pic" });
>>                 }
>> 
>>                 card.createEl("p", {
>>                     text: sim.file.name,
>>                     cls: "related-sim-name"
>>                 });
>>             }
>>         } else {
>>             dv.paragraph("No related sims found.");
>>         }
>>     }
>> }
>> ```
>>
>>
>>
>
>
>






```dataviewjs
const file = app.workspace.getActiveFile();
const char = dv.page(file?.path);
dv.container.empty();
if (!char) {
    dv.paragraph("⏳ carregando...");
} else {
    const simPath = char.file.path;

    const events = dv.pages('"Events"')
        .where(e => e.Participants?.some(p => p?.path === simPath));
	
	const titleEl = dv.container.createEl("div", { cls: "gallery-title" }); 
	const iconEl = titleEl.createEl("span", { cls: "gallery-title-icon" }); obsidian.setIcon(iconEl, "calendar-days"); // qualquer nome do lucide.dev 
	titleEl.createEl("span", { text: " Important Events" });

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






>[!Tags]
>