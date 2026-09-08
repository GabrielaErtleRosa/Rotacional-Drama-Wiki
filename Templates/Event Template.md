---
fileClass: EventClass
Participants:
Description:
cover:
Round:
tags:
  - Wedding
gallery:
cssclasses:
  - event-template
---


> [!event-cover]
> ![[BellaGoth.png]]


> [!event-description]
> ```dataviewjs
> const file = app.workspace.getActiveFile();
> const ev = dv.page(file?.path);
> dv.container.empty();
> dv.paragraph(ev?.Description ?? "Sem descrição ainda.");
> ```

> [!event-gallery]
> ```dataviewjs
> const file = app.workspace.getActiveFile();
> const ev = dv.page(file?.path);
> dv.container.empty();
>
> if (!ev) {
>     dv.paragraph("⏳ carregando...");
> } else {
>     const container = dv.container.createDiv({ cls: "sim-photo-gallery" });
>
>     const addBtn = container.createEl("button", { text: "+ Add photo", cls: "gallery-add-btn" });
>     addBtn.addEventListener("click", () => {
>         const input = document.createElement("input");
>         input.type = "file";
>         input.accept = "image/*";
>         input.addEventListener("change", async () => {
>             const f = input.files[0];
>             if (!f) return;
>             const buffer = await f.arrayBuffer();
>             const destPath = `Assets/Event-gallery/${f.name}`;
>             if (!app.vault.getAbstractFileByPath(destPath)) {
>                 await app.vault.createFolder("Assets/Event-gallery").catch(() => {});
>                 await app.vault.createBinary(destPath, buffer);
>             }
>             await app.fileManager.processFrontMatter(file, fm => {
>                 if (!fm.gallery) fm.gallery = [];
>                 if (!fm.gallery.includes(f.name)) fm.gallery.push(f.name);
>             });
>         });
>         input.click();
>     });
>
>     const grid = container.createDiv({ cls: "sim-photo-grid" });
>     const photos = ev.gallery ?? [];
>     for (const photo of photos) {
>         const imgFile = app.metadataCache.getFirstLinkpathDest(photo, file.path);
>         if (!imgFile) continue;
>         const src = app.vault.getResourcePath(imgFile);
>         const card = grid.createDiv({ cls: "sim-photo-card" });
>         card.createEl("img", { attr: { src } });
>     }
> }
> ```