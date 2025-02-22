

```dataviewjs

dv.span("** 😊 Rating  😥**")

const hue1 = 13 //red
const hue2 = 132 //green

const calendarData = {
    //year: 2022, // optional, remove this line to autoswitch year 
    intensityScaleStart: 1,
    intensityScaleEnd: 9,
    colors: {
        red2green: [
            `hsl(${hue1}, 100%, 37%)`,     // 1 - darkest red
            `hsl(${hue1}, 100%, 50%)`,     // 2 - 
            `hsl(${hue1}, 100%, 60%)`,     // 3 - 
            `hsl(${hue1}, 100%, 77%)`,     // 4 - lightest red
            `hsl(0, 0%, 80%)`,             // 5 - neutral gray
            `hsl(${hue2*0.7}, 70%, 72%)`,  // 6 - lightest green
            `hsl(${hue2*0.85}, 43%, 56%)`, // 7 - 
            `hsl(${hue2}, 49%, 36%)`,      // 8 - 
            `hsl(${hue2}, 59%, 24%)`,      // 9 - darkest green
        ],
    },
    entries: []
}

for(let page of dv.pages('"050_ReadingNotes"').where(p=>p.Rating)){ 

    calendarData.entries.push({
        date: page.file.name, 
        intensity: page.rating,
        content: await dv.span(`[](${page.file.name})`), //for hover preview
    })
      
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataview
table author, date, rating, tags
from #clippings 
```


```dataview 
list
```


