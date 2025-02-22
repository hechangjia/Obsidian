---
title: Habit Tracker Calendar
description: A HeatMap Calendar for tracking habits
tags:
  - 总结
categories: 日记
created: 2025-02-22
rating: "8"
---
[相关颜色代码](https://www.color-hex.com/popular-colors.php)


```dataviewjs

dv.span("**🏋️ Exercise 🏋️**")

const calendarData = {
    year: 2025, // optional, remove this line to autoswitch year
    colors: {
        red: ["#ff9e82","#ff7b55","#ff4d1a","#e73400","#bd2a00","#00FFFF"]
    },
    entries: []
}

for(let page of dv.pages('"040_Dairy"').where(p=>p.Exercise)){
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.Exercise,
        content: await dv.span(`[](${page.file.name})`), //for hover preview
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```


```dataviewjs

dv.span("** 😊 Mood  😥**")

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

for(let page of dv.pages('"040_Dairy"').where(p=>p.Mood)){ 

    calendarData.entries.push({
        date: page.file.name, 
        intensity: page.Mood,
        content: await dv.span(`[](${page.file.name})`), //for hover preview
    })
      
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs

dv.span("**😊 Daily Mood  😥**")

const calendarData = {
    year: 2025,
    colors: {
        blue: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"]
    },
    entries: [],
    showCurrentDayBorder: false
}

for(let page of dv.pages('"040_Dairy"').where(p=>p.Mood)){
	dv.paragraph(page.file.name + " Daily: " + page.Mood)
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.Mood
    })  
}

renderHeatmapCalendar(this.container, calendarData)

```

![](https://youtu.be/2U4kizMyEEc?si=dshIS5FUwQbyU6BR)

