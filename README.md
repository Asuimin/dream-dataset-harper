# π€ Dream Database

### π Profile

|Nationality|Occupation|
|:---|:---|
|Japan|Programmer|

### π Sheet List

|Sheet Name|θ‘¨ε|Tab-separated values|
|:---|:---|:---|
|story|πη©θͺ|story.tsv|
|fiscal-year|πεΉ΄εΊ¦|[fiscal-year.tsv](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)|
|famous-people|π€΄ζεδΊΊ|[famous-people.tsv](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/famous-people.tsv)|
|animal|πηη©|[animal.tsv](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/animal.tsv)|
|animal-classification|πηη©γ°γ«γΌγ|[animal-classification.tsv](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/animal-classification.tsv)|
|fictitious-people.tsv|πΊγ­γ£γ©γ―γΏγΌ|fictitious-people.tsv|
|pokemon|π£γγ±γ’γ³|[pokemon.tsv](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/pokemon.tsv)|
|pokemon-region|π£γγ±γ’γ³γ°γ«γΌγ|[pokemon-region.tsv](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/pokemon-region.tsv)|
|place|πε ΄ζ|place.tsv|
|sum-total|βεθ¨|[sum-total.tsv](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/sum-total.tsv)|
|music|πΌι³ζ₯½|music.tsv|

## π story η©θͺ

```mermaid
flowchart TD
  story.wake-up-date --"=TEXT(x,βdddβ)"--> story.wake-up-day-of-the-week
  story.wake-up-date --"=YEAR(EDATE(x,-3))"--> story.fiscal-year
  story.wake-up-date --"=YEAR(x)"--> story.year
  story.story --"=LEN(x)"--> story.word-count-in-story
  story.word-count-in-story --"=RANK(x,x-list,0)"--> story.word-count-in-story-rank
  story.story --"=ARRAYFORMULA(IF(COUNTIF(x,β*βοΌy-listοΌβ*β)=0,,y-list))"--> story.real-people
  real-people.name --"[y]"--> story.real-people
  story.fiscal-year ---> story.grade
```

```mermaid
flowchart TD
  story.wake-up-time
  story.post-date
  story.post-time
  story.data-registration-date
  story.animal
  story.fictitious-people
  story.uuid
```

## π fiscal-year εΉ΄εΊ¦

```mermaid
flowchart TD
  fiscal-year.start-date --"=YEAR(x)"--> fiscal-year.fiscal-year --> fiscal-year.grade
  fiscal-year.fiscal-year --"=COUNTIF(y-list,x)"--> fiscal-year.dreams
  story.fiscal-year --"[y]"--> fiscal-year.dreams
  fiscal-year.fiscal-year --"[z]"--> fiscal-year.days-to-dream
  story.fiscal-year --"[y]"--> fiscal-year.days-to-dream
  story.wake-up-date --"=COUNTA(UNIQUE(FILTER(x,y-list=z)))"--> fiscal-year.days-to-dream
  fiscal-year.fiscal-year --"[z]"--> fiscal-year.word-count-in-story
  story.fiscal-year --"[y]"--> fiscal-year.word-count-in-story
  story.word-count-in-story --"=SUM(FILTER(x,y-list=z))"--> fiscal-year.word-count-in-story
```

```mermaid
flowchart TD
  fiscal-year.start-date(ιε§ζ₯) --"=YEAR(x)"--> fiscal-year.fiscal-year(εΉ΄εΊ¦) --> fiscal-year.grade(ε­¦εΉ΄)
  fiscal-year.fiscal-year(εΉ΄εΊ¦) --"=COUNTIF(y-list,x)"--> fiscal-year.dreams(ε€’ζ°)
  story.fiscal-year(η©θͺγ?εΉ΄εΊ¦) --"[y]"--> fiscal-year.dreams(ε€’ζ°)
  fiscal-year.fiscal-year(εΉ΄εΊ¦) --"[z]"--> fiscal-year.days-to-dream(ε€’ζ₯ζ°)
  story.fiscal-year(η©θͺγ?εΉ΄εΊ¦) --"[y]"--> fiscal-year.days-to-dream(ε€’ζ₯ζ°)
  story.wake-up-date(η©θͺγ?θ΅·εΊζε») --"=COUNTA(UNIQUE(FILTER(x,y-list=z)))"--> fiscal-year.days-to-dream(ε€’ζ₯ζ°)
  fiscal-year.fiscal-year(εΉ΄εΊ¦) --"[z]"--> fiscal-year.word-count-in-story(η©θͺζε­ζ°)
  story.fiscal-year(η©θͺγ?εΉ΄εΊ¦) --"[y]"--> fiscal-year.word-count-in-story(η©θͺζε­ζ°)
  story.word-count-in-story(η©θͺγ?η©θͺζε­ζ°) --"=SUM(FILTER(x,y-list=z))"--> fiscal-year.word-count-in-story(η©θͺζε­ζ°)
```

## π animal ηγη©

```mermaid
flowchart TD
  story.animal --"=UNIQUE(TRANSPOSE(SPLIT(TEXTJOIN(β/β,,x-list),β/β)))"--> animal.name
  story.animal --"=COUNTIF(x-list,β*/βοΌyοΌβ/*β)"--> animal.appearance
  animal.name --"[y]"--> animal.appearance
  story.animal --"[z]"--> animal.date-of-appearance
  animal.name --"[y]"--> animal.date-of-appearance
  story.wake-up-date --"=X(x,y,z)=TEXTJOIN(β β,,FILTER(x-list,COUNTIFS(z-list,z-list,z-list,β*/βοΌyοΌβ/*β)))"--> animal.date-of-appearance
  story.animal --"[z]"--> uuid-of-appearance
  animal.name --"[y]"--> uuid-of-appearance
  story.uuid --"=X(x,y,z)"--> uuid-of-appearance
```

---

## π€΄ Real people appearing in dreams ε€’γ«εΊγ¦γγε?ε¨γ?δΊΊη©

### π Friend ει

|Portrait painting<br>δΊΊη©η»|Summary ζ¦θ¦|
|:---:|:---|
|![Alexander](https://github.com/Asuimin/dream-dataset-harper/blob/main/image/real-people/Alexander-360px.png)<br>Alexander<br>γ’γ¬γ­γ΅γ³γγΌ<br><br>Buddy θ¦ͺε|He has the strongest number of appearances among his friends. Until FY2020, he and Sam were rivals in the number of appearances, but in FY2021, he won by an overwhelming margin. Among his friends, he has the highest number of appearances in FY 2016, FY 2017 (tied for first place), FY 2018, FY 2020 (tied for first place), and FY 2021.<br>γειγ?δΈ­γ§γζεΌ·γθͺγη»ε ΄ζ°γδ»εΎγε½Όγ?η»ε ΄ζ°γθΆγγειγ―ηΎγγͺγγ¨ζγγγγ2020εΉ΄εΊ¦γΎγ§γ―γ΅γ γ¨η»ε ΄ζ°γη«Άγεγγ©γ€γγ«γ γ£γγγ2021εΉ΄εΊ¦γ―ε§εηγͺε·?γ§εε©γγ¦γγγειγ?δΈ­γ§γ―2016εΉ΄εΊ¦γ2017εΉ΄εΊ¦(εη1δ½)γ2018εΉ΄εΊ¦γ2020εΉ΄εΊ¦(εη1δ½)γ2021εΉ΄εΊ¦γ?η»ε ΄ζ°γ1δ½γ<br><br>![crown](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/image/crown/Alexander.svg)|
|![Sam](https://github.com/Asuimin/dream-dataset-harper/blob/main/image/real-people/Sam-360px.png)<br>Sam γ΅γ <br><br>Buddy θ¦ͺε|He was a competitor with Alexander for the number of appearances until FY2020. Among friends, he ranked first in appearances in FY 2014, FY 2015, FY 2017 (tied for first), FY 2019, and FY 2020 (tied for first).<br>γ2020εΉ΄εΊ¦γΎγ§γ―γ’γ¬γ­γ΅γ³γγΌγ¨η»ε ΄ζ°γη«Άγεγγ©γ€γγ«γ γ£γγειγ?δΈ­γ§γ―2014εΉ΄εΊ¦γ2015εΉ΄εΊ¦γ2017εΉ΄εΊ¦(εη1δ½)γ2019εΉ΄εΊ¦γ2020εΉ΄εΊ¦(εη1δ½)γ?η»ε ΄ζ°γ1δ½γ<br><br>![crown](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/image/crown/Sam.svg)|
|Carlos γ«γ«γ­γΉ<br><br>Buddy θ¦ͺε|2021εΉ΄εΊ¦γ―2020εΉ΄εΊ¦γ¨ζ―γΉγ¦εΊηΎεζ°γη΄2εγε’γγ¦γγγειγ?δΈ­γ§γ―2015εΉ΄εΊ¦γ?η»ε ΄ζ°γ2δ½γ2016εΉ΄εΊ¦γ?η»ε ΄ζ°γ3δ½γ|

---

## π­ Dreams & Days to dream ε€’ζ°γ¨ε€’ζ₯ζ°

![dreams](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/dreams.svg)

### [π Figure. Dreams & Days to dream ε€’ζ°γ¨ε€’ζ₯ζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

![dreams](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/month/dreams-per-month.svg)

### π Figure. Dreams per month ζγγ¨γ?ε€’ζ°

### Table. Dreams per month ζγγ¨γ?ε€’ζ°

|εΉ΄εΊ¦ Fiscal year|4ζ Apr.|5ζ May|6ζ Jun.|7ζ Jul.|8ζ Aug.|9ζ Sep.|10ζ Oct.|11ζ Nov.|12ζ Dec.|1ζ Jan.|2ζ Feb.|3ζ Mar.|
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
|2007|1|2|0|0|0|0|0|0|0|0|0|0|
|2009|0|0|1|0|0|0|0|0|0|0|0|0|
|2013|0|2|0|2|1|0|0|0|1|0|0|0|
|2014|2|1|1|0|1|0|0|0|1|0|1|2|
|2015|0|3|1|1|0|0|0|0|1|3|0|1|
|2016|1|1|2|4|13|2|1|0|16|24|8|7|
|2017|5|6|3|3|1|4|3|2|1|1|2|2|
|2018|5|4|4|1|4|4|25|27|9|7|13|14|
|2019|21|15|14|11|21|10|11|1|3|3|2|12|
|2020|29|10|12|19|36|49|59|71|43|51|36|35|
|2021|49|42|31|34|49|74|42|43|30|40|46|67|

### Table. Dream diary period ε€’ζ₯θ¨ζ

|ποΈ ε€’ζ₯θ¨ζ|ποΈ Dream diary period|ζ Month(YYYY/MM)|
|:---|:---|:---|
|η¬¬δΈζ¬‘ε€’ζ₯θ¨ζ|First dream diary period|2016/08, 2016/12-2017/01|
|η¬¬δΊζ¬‘ε€’ζ₯θ¨ζ|Second dream diary period|2018/10-2019/10|
|η¬¬δΈζ¬‘ε€’ζ₯θ¨ζ|Third dream diary period|2020/04, 2020/08-|

![dreams](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/month/dreams-per-month-comment.svg)

### π Figure. Dreams per month ζγγ¨γ?ε€’ζ°

---

## π Word count ζε­ζ°

### π₯οΈ Source code γ½γΌγΉγ³γΌγ

|Name|Variable|Source code|
|:---|:---|:---|
|Dream Characters|word-count.word-count|=COUNT(FILTER(story.word-count-list, story.word-count-list > word-count.word-count-min, story.word-count-list <= word-count.word-count-max))|
|Word count|fiscal-year.word-count|=SUM(FILTER(story.word-count-list, story.fiscal-year-list=fiscal-year.fiscal-year))|
|Average Word count|fiscal-year.average-word-count|=fiscal-year.word-count/fiscal-year.dreams|

|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/dreams-separated-by-every-15-characters.svg)|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/dreams-separated-by-every-25-characters.svg)|
|:---|:---|
|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/dreams-separated-by-every-50-characters.svg)|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/dreams-separated-by-every-100-characters.svg)|

### π Figure. Dream Characters ε€’γ?ζε­ζ°

|![word count](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/word-count.svg)|![word count](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/word-count-log-scale.svg)|
|:---|:---|

### [π Figure. Word count ζε­ζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

![word count](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/average-word-count.svg)

### [π Figure. Average word count εΉ³εζε­ζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/word-count-in-story-and-year.svg)|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/word-count-in-story-and-year-2013.svg)|
|:---|:---|
|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/word-count-in-story-and-year-2018.svg)|![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/word-count-in-story-and-year-2020.svg)|

### π Figure. Word count in story and year η©θͺζε­ζ°γ¨εΉ΄

![story](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/story/word-count-in-story-and-rank.svg)

### π Figure. Word count in story and rank η©θͺζε­ζ°γ¨ι δ½

---

## π Day-of-week ζζ₯

|![day of the week](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/dreams-per-day-of-the-week.svg)|![day of the week](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/percentage-of-dreams-per-day-of-the-week.svg)|
|:---|:---|

### [π Figure. Dreams per day of the week ζζ₯γγ¨γ?ε€’ζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

|![day of the week](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/day-of-week-deviation-score.svg)|![day of the week](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/percentage-of-dreams-per-day-of-the-week-scatter-plot.svg)|
|:---|:---|

### [π Figure. Day-of-week deviation score ζζ₯γγ¨γ?ε€’ζ°γ?εε·?ε€](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)
### [π Figure. Percentage of dreams per day of the week ζζ₯γγ¨γ?ε€’ζ°ε²ε](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

|![day of the week](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/day-of-week-coefficient-of-variation.svg)|![day of the week](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/day-of-week-coefficient-of-variation-2013.svg)|
|:---|:---|

### [π Figure. Day-of-week coefficient of variation ζζ₯γγ¨γ?ε€’ζ°γ?ε€εδΏζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

---

## π§ Real people ε?ε¨δΊΊη©

|![real people](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/total-number-of-real-people.svg)|![real people](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/total-number-of-real-people-log-scale.svg)|
|:---|:---|

### [π Figure. Total number of real people who appear in dreams ε€’γ«η»ε ΄γγε?ε¨δΊΊη©γ?ε»ΆγΉδΊΊζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

![real people](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/total-number-of-real-people-per-dream.svg)

### [π Figure. Total number of real people who appear in dreams per dream 1ε€’γγγγ?ε€’γ«η»ε ΄γγε?ε¨δΊΊη©γ?ε»ΆγΉδΊΊζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

---

## π Animal ηγη©

![animal](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/probability-of-animal-appearing.svg)

### [π Figure. Probability of animal appearing ηη©γη»ε ΄γγη’Ίη](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

![animal](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/animal/probability-of-appearance-by-animal-classification.svg)

### [π Figure. Probability of appearance by animal classification ηη©γ?ει‘γγ¨γ?η»ε ΄η’Ίη](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/animal-classification.tsv)

![animal](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/animal/ratio-of-animal-classification.svg)

### [π Figure. Ratio of animal classification ηη©γ?ει‘γγ¨γ?ε²ε](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/animal-classification.tsv)

---

## πΊ Fictitious people γ­γ£γ©γ―γΏγΌ(ζΆη©Ίγ?δΊΊη©)

|![fictitious people](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/probability-of-fictitious-people-appearing.svg)|![probability](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/probability-of-appearance.svg)|
|:---|:---|

### [π Figure. Probability of fictitious people appearing γ­γ£γ©γ―γΏγΌοΌζΆη©Ίγ?δΊΊη©οΌγη»ε ΄γγη’Ίη](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

---

## π£ PokΓ©mon γγ±γ’γ³

![pokemon](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/pokemon-related-dreams-per-dream.svg)

### [π Figure. PokΓ©mon-related dreams per dream 1ε€’γγγγ?γγ±γ’γ³ι’ι£γ?ε€’ζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

|![pokemon](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/pokemon/pokemon-appearance-ratios-for-each-region.svg)|![pokemon](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/pokemon/pokemon-appearance-ratios-for-each-region-donuts.svg)|
|:---|:---|

### [π Figure. PokΓ©mon appearance ratios for each region εε°ζΉγ?γγ±γ’γ³γ?εΊηΎη](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/pokemon-region.tsv)

---

# πΌ Music ι³ζ₯½

![music](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/fiscal-year/musical-dreams.svg)

### [π Figure. Musical dreams ι³ζ₯½ε€’ζ°](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/fiscal-year.tsv)

![music](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/music/percentage-of-key.svg)

### [π Figure. Percentage of key ε€’γ§ζ΅γγι³ζ₯½γ?θͺΏγ?ε²ε](https://github.com/Asuimin/dream-dataset-harper/tree/main/data/sheet-music)

|![music](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/music/music-with-a-fixed-key-signature.svg)|![music](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/music/music-with-a-fixed-key-signature-donuts.svg)|
|:---|:---|

### [π Figure. Music with a fixed key signature θͺΏε·γη’Ίε?γγι³ζ₯½](https://github.com/Asuimin/dream-dataset-harper/tree/main/data/sheet-music)

|![music](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/music/all-music-key-signatures.svg)|![music](https://raw.githubusercontent.com/Asuimin/dream-dataset-harper/main/graph/music/all-music-key-signatures-donuts.svg)|
|:---|:---|

### [π Figure. All music key signatures ε¨γ¦γ?ι³ζ₯½γ?θͺΏε·](https://github.com/Asuimin/dream-dataset-harper/tree/main/data/sheet-music)

---

### π΅ MIDI list

|Date (YYYY/MM/DD)|MIDI Download|
|:---|:---|
|2018/04/14|[Download](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/sheet-music/2018/0414-01/2018-0414-01.mid?raw=true)|
|2018/05/20|[Download](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/sheet-music/2018/0520-01/2018-0520-01.mid?raw=true)|
|2018/08/10|[Download](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/sheet-music/2018/0810-02/2018-0810-02.mid?raw=true)|
|2018/08/12|[Download](https://github.com/Asuimin/dream-dataset-harper/blob/main/data/sheet-music/2018/0812-01/2018-0812-01.mid?raw=true)|

---

### πΌ Musical Score

|![musical score 1](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/sheet-music/all-decoration/DreamAll-1.png)|![musical score 2](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/sheet-music/all-decoration/DreamAll-2.png)|
|:---|:---|
|![musical score 3](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/sheet-music/all-decoration/DreamAll-3.png)||

---

## π Dream diary continuation years (as of September 2021) ε€’ζ₯θ¨γ?ηΆηΆεΉ΄ζ°οΌ2021εΉ΄9ζηΎε¨οΌ

The first dream diary I wrote was the dream of April 6, 2007 (at least this dream is the oldest extant dream diary I wrote). Considering this day as a starting point, it has been 14 years since I started keeping a dream diary.

However, no dreams have been recorded during the subsequent 2008, 2010-2012 period. Therefore, it is hard to say that I have been keeping a dream diary for 14 years.

Let's calculate the dream diary history from the first day when you start to continue the dream diary. It was December 6, 2015 that I started writing a dream diary more than once a month. Starting from this day, it's been five and a half years since I started keeping a dream diary. It's longer than I expected.

In summary, the dream diary history is five and a half years in the narrow sense and 14 years in the broadest sense.

η§γεγγ¦ζΈγθ¨γγε€’ζ₯θ¨γ―2007εΉ΄4ζ6ζ₯γ?ε€’γ§γγοΌε°γͺγγ¨γγγγ?ε€’γη§γ?ζΈγγηΎε­γγζε€γ?ε€’ζ₯θ¨γ¨γͺγγΎγοΌγγγ?ζ₯γθ΅·ηΉγ«θγγγ¨η§γ―ε€’ζ₯θ¨γδ»γε§γγ¦γγ14εΉ΄γη΅ιγγγγ¨γ«γͺγγΎγγ

γγγγγγ?εΎγ?2008εΉ΄γ2010εΉ΄γγ2012εΉ΄γ?ζιγ―δΈεΊ¦γε€’γθ¨ι²γγγ¦γγΎγγγγγ?γγγη§γ―ε€’ζ₯θ¨γ14εΉ΄γηΆγγ¦γγγ¨γ―θ¨γι£γγ§γγ

ε€’ζ₯θ¨γηΆηΆγε§γγζεγ?ζ₯γγε€’ζ₯θ¨ζ­΄γη?εΊγγγγ¨γ«γγΎγγγγ1γΆζγ«1εΊ¦δ»₯δΈγ?ι »εΊ¦γ§ε€’ζ₯θ¨γζΈγε§γγγ?γ2015εΉ΄12ζ6ζ₯γ§γγγγ?ζ₯γθ΅·ηΉγ«θγγγ¨η§γ―ε€’ζ₯θ¨γδ»γε§γγ¦γγ5εΉ΄εγη΅ιγγγγ¨γ«γͺγγΎγγζγ£γγγγι·γγ§γγ

γΎγ¨γγγ¨γε€’ζ₯θ¨ζ­΄γ―η­ηΎ©γ γ¨5εΉ΄εγζεΊηΎ©γ γ¨14εΉ΄γ¨γͺγγΎγγ

## π΅ About the music that played in my dream ε€’γ§ζ΅γγι³ζ₯½γ«γ€γγ¦

I sometimes have music playing in my dreams. I categorize the music that plays in my dreams into two types. One is music that I know, and the other is music that I don't know. I can understand that the music I know is stored in my brain, but where does the music I don't know come from?

I have compiled the unknown songs played in my dream as music score data. The score data is available in musicxml format. [Please feel free to send me an issue if you have any other data format that you would like to see.](https://github.com/Asuimin/dream-database/issues)

η§γ―γγΎγ«ε€’γ§ι³ζ₯½γζ΅γγγγ¨γγγγΎγγη§γ―ε€’γ§ζ΅γγι³ζ₯½γ2η¨?ι‘γ«ει‘γγ¦γγΎγγγγγ―η₯γ£γ¦γγζ²γ¨η₯γγͺγζ²γ?2η¨?ι‘γ§γγη₯γ£γ¦γγζ²γζ΅γγγ?γ―γγ?ζ²γθ³γ«θ¨ζΆγγγ¦γγγ¨γͺγγ¨γͺγηθ§£γεΊζ₯γΎγγγη₯γγͺγζ²γ―δΈδ½γ©γγγηζγγγ¦γγγ?γ§γγγγγ

ε€’γ§ζ΅γγη₯γγͺγζ²γζ₯½θ­γγΌγΏγ¨γγ¦γΎγ¨γγ¦γγγΎγγζ₯½θ­γγΌγΏγ―musicxmlε½’εΌγ§ε¬ιγγ¦γγΎγγδ»γ«γγγ¨ε¬γγγγΌγΏε½’εΌγͺγ©γγγγΎγγγγζ°θ»½γ«Issueγι£γ°γγ¦γγ γγγ


## π§  About lucid dreaming ζζ°ε€’γ«γ€γγ¦

I first learned about lucid dreaming on Monday, April 6, 2015 at 8:17 am. I kept a dream diary before I knew lucid dreaming (at least 18 dreams have been recorded by April 6, 2015).

Records show that I have lucid dreaming at least twice. It is recorded that both of them were scary dreams. In a scary dream, I realized that it was a dream and was trying to wake up from it as soon as possible.

Therefore, I have no good memories of lucid dreaming.

η§γεγγ¦ζζ°ε€’γη₯γ£γγ?γ―2015εΉ΄4ζ6ζ₯οΌζοΌγ?εε8ζ17εγ§γγη§γ―ζζ°ε€’γη₯γεγγε€’ζ₯θ¨γγ€γγ¦γγΎγγοΌε°γͺγγ¨γ2015εΉ΄4ζ6ζ₯γΎγ§γ«18δ»Άγ?ε€’γ?θ¨ι²γγγγΎγοΌγ

θ¨ι²γ«γγγ¨η§γ―ε°γͺγγ¨γ2εγζζ°ε€’γθ¦γ¦γγΎγγγγ?2εγ¨γζγε€’γ γ£γγ¨θ¨ι²γγγ¦γγΎγγζγε€’γ?δΈ­γ§ε€’γ γ¨ζ°γ₯γγγγ‘ζ©γε€’γγθ¦γγγγ¨γγ¦γγγ?γ§γγ

γγ?γγγη§γ―ζζ°ε€’γ«θ―γζγεΊγγγγΎγγγ

---

### π­ Dream Contributions

![2007](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2007.svg)
![2009](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2009.svg)
![2013](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2013.svg)
![2014](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2014.svg)
![2015](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2015.svg)
![2016](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2016.svg)
![2017](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2017.svg)
![2018](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2018.svg)
![2019](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2019.svg)
![2020](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2020.svg)
![2021](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2021.svg)
![2022](https://raw.githubusercontent.com/Asuimin/image-archive/main/data/contributions-graph/v1/2022.svg)

---

## [π³ License γ©γ€γ»γ³γΉ](https://github.com/Asuimin/dream-database/blob/main/LICENSE)

[>> View License](https://github.com/Asuimin/dream-database/blob/main/LICENSE)

These data are licensed under CC BY 4.0.

γγγγ?γγΌγΏγ―CC BY 4.0γ§γ©γ€γ»γ³γΉγγγ¦γγΎγγ

Copyright (c) 2007-2022 As Project.
