### ListRow

ListRow Component with a standard variant and a variant with the link as shown below.

### Props

```table
span: 6
rows:
  - Prop: rowItem
    Type: object
    Notes: Required
  - Prop: index
    Type: number
    Notes: Required
  - Prop: onOverflowClick
    Type: func
    Notes: Required
  - Prop: children
    Type: node
    Notes: Optional. Default is null.
  - Prop: onExpandShow
    Type: one of either "title" or "subTitle"
    Notes: Optional. Default is "subTitles"
  - Prop: onExpandItem
    Type: "func({ index: number }): void"
    Notes: Optional. This is called when a user clicks "expand row" chevron
  - Prop: onCollapseItem
    Type: "func({ index: number }): void"
    Notes: Optional. This is called when a user clicks "collapse row" chevron
```

### ListContainer

Container Component which contains all the ListRows and is responsible for managing the expand or collapse state for the row.

### Props

```table
span: 6
rows:
  - Prop: children
    Type: node
    Notes: Optional. Default is null.
  - Prop: onRowCollapse
    Type: func
    Notes: Optional.
  - Prop: onModalClose
    Type: func
    Notes: Optional.
  - Prop: expandMultiple
    Type: boolean
    Notes: Optional. If true, multiple list rows can be expanded simultaneously. If false, only a single list row can be expanded at one time. Default is false.
```

### RowItem Prop Table

```table
span: 6
rows:
  - Prop: title
    Type: String
    Notes: Required
  - Prop: subTitle
    Type: String
    Notes: Required
  - Prop: dateTitle
    Type: String
    Notes: Required
  - Prop: dateSubTitle
    Type: String
    Notes: Required
  - Prop: url
    Type: String
    Notes: optional. Default is "".
  - Prop: buttonText
    Type: String
    Notes: Required
  - Prop: buttonVariant
    Type: String
    Notes: Optional. Determines button style variant. Possible variants are `standard`, `special`, `outline`, `transparent`. Default is `standard`
  - Prop: variant
    Type: String
    Notes: Required. Value is one of ["standard", "withLink"]
  - Prop: label
    Type: String
    Notes: Optional. Label text. Default is ""
  - Prop: labelVariant
    Type: Number
    Notes: Optional. Determines label style variant. Possible variants are `default`, `positive`, `alert`. Default is `default`
  - Prop: linkTitle
    Type: String
    Notes: Optional. Default is ""
  - Prop: linkUrl
    Type: String
    Notes: Optional. Default is ""
  - Prop: dateColor
    Type: String
    Notes: Optional. Default is "#262626"
  - Prop: onClick
    Type: func
    Notes: Required
```

### Standard List Row

```react
responsive: true
---
<ListContainer>
  <ListRow
    rowItem={{
        ...listItems[0],
        variant: "withLink",
        linkTitle: "Ticket Options Available",
        linkUrl: "",
        linkSubTitle: "on Partner Site",
        label: "On sale: MON \u2022 AUG 27 \u2022 10 AM",
        labelVariant: "positive"
    }}
    index={0}
    onOverflowClick={() => alert('Overflow Clicked')}
    onExpandItem={({index}) => alert(`Expand ${index}`)}
    onCollapseItem={({index}) => alert(`Collapse ${index}`)}
  />

  <ListRow
    rowItem={listItems[0]}
    index={1}
    onOverflowClick={() => alert('Overflow Clicked')}
    onExpandItem={({index}) => alert(`Expand ${index}`)}
    onCollapseItem={({index}) => alert(`Collapse ${index}`)}
  />
 </ListContainer>
```

### Multiple List Row with the Container

```react
responsive: true
---

<ListContainer expandMultiple={true}>
  <ListRow
    rowItem={{
            ...listItems[0],
            variant: "withLink",
            linkTitle: "Ticket Options Available",
            linkUrl: "",
            linkSubTitle: "on Partner Site"
        }}
    index={0}
    onOverflowClick={()=>{}}
  >
    <ListRowOverflow>
    {sections.map(section =>
        <Section title={section.title} medium={MAX_COLUMNS / sections.length} key={section.key}>
          {section.items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
        </Section>
        )}
    </ListRowOverflow>
 </ListRow>

  <ListRow rowItem={listItems[1]} index={1} onOverflowClick={()=>{}}>
    <ListRowOverflow>
      <Section title={sections[0].title} medium={MAX_COLUMNS / sections.length} key={sections[0].key}>
          {sections[0].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
       <Section title={sections[1].title} medium={MAX_COLUMNS / sections.length} key={sections[1].key}>
          {sections[1].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
    </ListRowOverflow>
  </ListRow>


  <ListRow rowItem={listItems[2]} index={2} onOverflowClick={()=>{}}>
    <ListRowOverflow>
     <Section title={sections[0].title} medium={MAX_COLUMNS / sections.length} key={sections[0].key}>
          {sections[0].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
       <Section title={sections[1].title} medium={MAX_COLUMNS / sections.length} key={sections[1].key}>
          {sections[1].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
      <Section title={sections[2].title} medium={MAX_COLUMNS / sections.length} key={sections[2].key}>
          {sections[2].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
    </ListRowOverflow>
  </ListRow>

  <ListRow rowItem={listItems[3]} index={3} onOverflowClick={()=>{}}>
    <ListRowOverflow>
     <Section title={sections[0].title} medium={MAX_COLUMNS / sections.length} key={sections[0].key}>
          {sections[0].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
       <Section title={sections[1].title} medium={MAX_COLUMNS / sections.length} key={sections[1].key}>
          {sections[1].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
      <Section title={sections[2].title} medium={MAX_COLUMNS / sections.length} key={sections[2].key}>
          {sections[2].items.map(item =>
          <SectionItem item={item} key={item.title}/>)}
      </Section>
    </ListRowOverflow>
  </ListRow>

</ListContainer>
;
```

### Standard expanded List Row

```react
responsive: true
---
<ListContainer>
 <ListRow rowItem={listItems[0]} index={0} onOverflowClick={()=>{}}>
 <ListRowOverflow>
 {sections.map(section =>
    <Section title={section.title} large={MAX_COLUMNS / sections.length} key={section.key}>
      {section.items.map(item =>
      <SectionItem item={item} key={item.title}/>)}
    </Section>
    )}
</ListRowOverflow>
 </ListRow>
 </ListContainer>
```

### List Row with Link

```react
responsive: true
---
<ListContainer>
 <ListRow
         rowItem={{
           ...listItems[0],
           variant: "withLink",
           linkTitle: "Ticket Options Available",
           linkUrl: "",
           linkSubTitle: "on Partner Site"
         }}
         index={0}
         onOverflowClick={()=>{}}
       />
 </ListContainer>
```

### List Row with Label

```react
responsive: true
---
<ListContainer>
 <ListRow
    rowItem={{
      ...listItems[0],
      label: "custom label",
    }}
    index={0}
    onOverflowClick={()=>{}}
  >
    <ListRowOverflow>
      <Section title={sections[0].title} medium={MAX_COLUMNS / sections.length} key={sections[0].key}>
        {sections[0].items.map(item =>
        <SectionItem item={item} key={item.title}/>)}
      </Section>
       <Section title={sections[1].title} medium={MAX_COLUMNS / sections.length} key={sections[1].key}>
        {sections[1].items.map(item =>
        <SectionItem item={item} key={item.title}/>)}
      </Section>
    </ListRowOverflow>
  </ListRow>
  <ListRow
    rowItem={{
      ...listItems[0],
      label: "On sale: MON \u2022 AUG 27 \u2022 10 AM",
      labelVariant: "positive"
    }}
    index={1}
    onOverflowClick={()=>{}}
  >
    <ListRowOverflow>
      <Section title={sections[0].title} medium={MAX_COLUMNS / sections.length} key={sections[0].key}>
        {sections[0].items.map(item =>
        <SectionItem item={item} key={item.title}/>)}
      </Section>
       <Section title={sections[1].title} medium={MAX_COLUMNS / sections.length} key={sections[1].key}>
        {sections[1].items.map(item =>
        <SectionItem item={item} key={item.title}/>)}
      </Section>
    </ListRowOverflow>
  </ListRow>
  <ListRow
    rowItem={{
      ...listItems[0],
      buttonText: "More Info",
      buttonVariant: "outline",
      label: "Sold out",
      labelVariant: "alert"
    }}
    index={2}
    onOverflowClick={()=>{}}
  >
    <ListRowOverflow>
      <Section title={sections[0].title} medium={MAX_COLUMNS / sections.length} key={sections[0].key}>
        {sections[0].items.map(item =>
        <SectionItem item={item} key={item.title}/>)}
      </Section>
       <Section title={sections[1].title} medium={MAX_COLUMNS / sections.length} key={sections[1].key}>
        {sections[1].items.map(item =>
        <SectionItem item={item} key={item.title}/>)}
      </Section>
    </ListRowOverflow>
  </ListRow>
 </ListContainer>
```

### List Row with Colored Date

```react
responsive: true
---

<ListContainer>
<ListRow
        rowItem={{
          ...listItems[0],
          variant: "standard",
          dateColor: "#C56BFF",
        }}
        index={0}
        onOverflowClick={()=>{}}
      />
</ListContainer>
```
