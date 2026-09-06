# All

```dataviewjs
const current = dv.current();

const events = dv.pages()
.where(e => e.round?.path?.includes(current.file.name));

const container = document.createElement("div");

container.className = "round-gallery";

for(let ev of events){

    let cover = "";

    if(ev.cover){

        const file = app.metadataCache.getFirstLinkpathDest(
            ev.cover.path ?? ev.cover,
            ev.file.path
        );

        if(file){
            cover = app.vault.getResourcePath(file);
        }
    }

    const card = document.createElement("div");

    card.className = "event-card";

    card.innerHTML = `

        <img src="${cover}">

        <div class="event-info">

            <div class="event-title">
                ${ev.file.name}
            </div>


            
            <strong>Description:</strong>
            
            <div class="event-description">

    ${
        ev.description
        ? (
            ev.description.length > 180
            ? ev.description.slice(0,180) + "..."
            : ev.description
        )
        : ""
    }

</div>
  
		
<div>  
<strong>Participants:</strong>  
  
${
    ev.participants
    ?.slice(0,3)

    .map(p =>
        p.path
        .split("/")
        .pop()
        .replace(".md","")
    )

    .join(", ")

    + (ev.participants?.length > 3 ? "..." : "")

    ?? ""
}
  
</div>

        </div>
    `;

    card.onclick = ()=>{
        app.workspace.openLinkText(
            ev.file.path,
            current.file.path
        );
    };

    container.appendChild(card);
}

dv.container.appendChild(container);
```



