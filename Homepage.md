---
icon:
  - 🥳
date: 2025-02-23-07-35
author:
  - charlie
description: Homepage
title: Homepage
categories:
  - 日记
  - 模板
tags:
  - homepage
created: 2025-02-23
Mood: "8"
Exercise: 
type: 日记
banner: "[[beamer图片1.png]]"
banner-display: cover
banner-height: 350
banner-x: 50
banner-y: 50
---

## Due today

> [!check] Due today
> ```tasks
>  due today
>  
> ```




## Tasks Not Done

> [!chaeck]
> ```tasks
> not done
> ```


## All Tasks

> [!check] Due today
> ```tasks
> ```

```dataview 
list 
from "040_Dairy"
```


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



# Picture

![photo by Jorge Salvador(https://unsplash.com/@jsshotz?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://images.unsplash.com/photo-1597211165861-29ef11229300?crop=entropy&cs=srgb&fm=jpg&ixid=M3w2NDU1OTF8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDAzMTA1MDl8&ixlib=rb-4.0.3&q=85)

![photo by Yoksel 🌿 Zok(https://unsplash.com/@yoksel?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://images.unsplash.com/photo-1613236116431-56bc4aabe4ce?crop=entropy&cs=srgb&fm=jpg&ixid=M3w2NDU1OTF8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDAzMTA1MTB8&ixlib=rb-4.0.3&q=85&w=200&h=200)

![photo by Joel Holland(https://unsplash.com/@joelholland?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://images.unsplash.com/photo-1470240731273-7821a6eeb6bd?crop=entropy&cs=srgb&fm=jpg&ixid=M3w2NDU1OTF8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDAzMTA1MDl8&ixlib=rb-4.0.3&q=85&w=200&h=200)

![photo by Luca Bravo(https://unsplash.com/@lucabravo?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://images.unsplash.com/photo-1508144753681-9986d4df99b3?crop=entropy&cs=srgb&fm=jpg&ixid=M3w2NDU1OTF8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDAzMTA1MDl8&ixlib=rb-4.0.3&q=85&w=200&h=200)