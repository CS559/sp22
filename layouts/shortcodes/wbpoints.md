{{/** get the appropriate workbook **/}} 
{{ $wb := index $.Site.Data.workbooks.workbook ( (.Get 0) | default 0) }}
{{/** need to use a scratch variable, not a real variable https://discourse.gohugo.io/t/counter-variables-and-template-scope/382/5 */}}
{{ $.Page.Scratch.Set "total" 0 }}
{{ range $wb.points }}
+ {{ .desc }} (Box: {{.box}}) (Points:{{.points}})
{{ $.Page.Scratch.Add "total" .points }}
{{ end }}
Regular Points: {{ $.Page.Scratch.Get "total" }}

{{ $.Page.Scratch.Set "totalbonus" 0 }}
{{ with $wb.bonus }}
{{ range . }}
+ {{ .desc }} (Box: {{.box}}) (Points:{{.points}})
{{ $.Page.Scratch.Add "totalbonus" .points }}
{{ end }}
{{ end }}

Bonus Points: {{ $.Page.Scratch.Get "totalbonus" }}
