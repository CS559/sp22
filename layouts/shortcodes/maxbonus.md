{{/** get the appropriate workbook **/}} 
{{- $wb := index $.Site.Data.workbooks.workbook ( .Site.Params.workbook | default 0) }}
{{- $wb.maxbonus -}}