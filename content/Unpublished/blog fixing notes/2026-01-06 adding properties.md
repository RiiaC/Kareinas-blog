1. Copied from **C:\Obsidian files\SEAD_structure_Obsidian\quartz.layout.ts** to **C:\Obsidian files\Kareinas-blog\quartz.layout.ts** the line that says:
> **Component.FrontmatterPropertiesBox(),**
2. This triggers an error message:
> ▲ WARNING Import "FrontmatterPropertiesBox" will always be undefined because there is no matching export in "quartz/components/index.ts" (import-is-undefined)
3. copied the file from **C:\Obsidian files\SEAD_structure_Obsidian\quartz\components\FrontmatterPropertiesBox.tsx** to **C:\Obsidian files\Kareinas-blog\quartz\components\FrontmatterPropertiesBox.tsx**
4. added to the index-ts file the lines:
> import FrontmatterPropertiesBox from "./FrontmatterPropertiesBox"
> and, under export "FrontmatterPropertiesBox,"
5. moved the properties box for my personal blog to the very bottom of the page (above the footers) by first deleting the edit in step 1. and then editing  **C:\Obsidian files\Kareinas-blog\quartz.layout.ts** to have a new section, below the "beforeBody" section., and before the "left" section, that says:
>   afterBody: [
    Component.FrontmatterPropertiesBox(),
  ],
6. in order to not display properties with null values, I edited the  **C:\Obsidian files\Kareinas-blog\quartz\components\FrontmatterPropertiesBox.tsx** to replace the "  **const entries = Object.entries(props)**" line with
````
```const entries = Object.entries(props).filter(([_, value]) => {
  if (value === null) return false
  if (value === undefined) return false
  if (Array.isArray(value) && value.length === 0) return false
  if (typeof value === "string" && value.trim() === "") return false
  return true
})
````
7. also edited the part that defines how lists are shown to include a space after commas by editing  the return section to show:
````
    <div class="frontmatter-box">
      <h3>Properties</h3>
      <ul>
        {entries.map(([key, value]) => (
          <li><strong>{key}:</strong> {Array.isArray(value) ? value.join(", ") : String(value)}</li>
        ))}
      </ul>
    </div>
```
