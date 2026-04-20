# Taller-Pr-ctico-02-Pliego-de-condiciones-para-desarrollo-de-MVP001

## *Consulta 1*
for $critica in //Vehiculo[@Estado = "En ruta"]
let $bateria := $critica/Bateria
let $matricula := $critica/Matricula
let $modelo := $critica/Modelo
let $html := 
  <html>
    <head>
      <title>Vehiculos con bateria critica</title>
      <meta charset="UTF-8"/>
    </head>
    <body>
      <h1>Listado de Vehiculos con bateria critica</h1>
      <ol>
      {
        for $critica in //Vehiculos[@Estado = "En ruta"]
        let $bateria := data($critica/Bateria)
        let $matricula := data($critica/Matricula)
        let $modelo := data($critica/Modelo)
        return
          <li>
            <strong>{ $matricula }</strong>
          </li>
      }
      </ol>
    </body>
  </html>
where $bateria < 15
return file:write("C:\Users\Sergio\Desktop\LDM\index.html",$html,
  map {
    "method": "html",
    "version": "5.0",
    "indent": "yes",
    "omit-xml-declaration": "yes",
    "encoding": "UTF-8"
  }
)
