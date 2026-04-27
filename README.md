# Taller-Pr-ctico-02-Pliego-de-condiciones-para-desarrollo-de-MVP001

## *Consulta 1*
let $html :=
  <html lang="es">
    <head>
      <title>Vehículos con batería crítica</title>
      <meta charset="UTF-8"/>
    </head>
    <body>
      <h1>Vehículos con batería crítica (&lt;15%) y en ruta</h1>
      <ol>
      {
        for $vehiculo in //Vehiculo[Estado = "En ruta"]
        let $bateria := number($vehiculo/Bateria)
        where $bateria < 15
        return
          <li>
            <strong>{ data($vehiculo/Matricula) }</strong>
            <ul>
              <li>Modelo: { data($vehiculo/Modelo) }</li>
              <li>Estado: { data($vehiculo/Estado) }</li>
              <li>Batería: { $bateria }%</li>
            </ul>
          </li>
      }
      </ol>
    </body>
  </html>
return file:write(
  "C:\Users\DAM1\Desktop\Taller2\consulta1.html",
  $html,
  map {
    "method": "html",
    "version": "5.0",
    "omit-xml-declaration": "yes",
    "encoding": "UTF-8",
    "indent": "yes"
  }
)
