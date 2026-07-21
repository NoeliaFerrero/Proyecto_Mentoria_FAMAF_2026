### Guía metodológica para la integración de fuentes de datos
Antes de escribir una sola línea de código, revisen la siguiente info. 
Esta matriz les permitirá comprender cómo se relacionan las distintas fuentes de información y definir la estrategia de integración de datos.

| Aspecto                                               | Pruebas Aprender                                      | Encuesta Permanente de Hogares (EPH)                    |
| ----------------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------- |
| **¿Qué representa una fila?**                         | Un estudiante evaluado                                | Una persona perteneciente a un hogar                    |
| **Unidad de análisis**                                | Estudiante                                            | Persona                                                 |
| **Identificador principal**                           | ID anónimo del estudiante                             | CODUSU + COMPONENTE                                     |
| **¿Existe un identificador común entre ambas bases?** | ❌ No                                                 |❌ No                                                   |
| **Nivel geográfico disponible**                       | Jurisdicción (y otras variables territoriales)        | Aglomerado / Provincia                                  |
| **Año seleccionado**                                  | 2024                                                  | 2024 (3.er trimestre)                                   |
| **Variables de integración**                          | Año + Jurisdicción (o el nivel geográfico compatible) | Año + Jurisdicción/Aglomerado                           |
| **Variables propias de la fuente**                    | Desempeño, sobreedad, inasistencias, NSE, etc.        | Ingresos, vivienda, empleo, composición del hogar, etc. |
| **Rol dentro del proyecto**                           | Fuente principal                                      | Fuente de contexto socioeconómico                       |


### Conclusión metodológica

Las Pruebas Aprender y la EPH no pueden vincularse a nivel individual, ya que no comparten un identificador común que permita relacionar un estudiante con un hogar específico.

Por este motivo, la integración se realizará utilizando variables de integración (como el año y el nivel geográfico compatible), incorporando al dataset de Aprender indicadores socioeconómicos agregados obtenidos a partir de la EPH.

De esta manera, Aprender será la fuente principal del proyecto, mientras que la EPH aportará información del contexto socioeconómico en el que se encuentran los estudiantes evaluados.

                    PRUEBAS APRENDER
                 (1 fila = 1 estudiante)
                           │
                           │
                           ▼
                  DATASET ANALÍTICO
                           ▲
                           │
                           │
           Indicadores socioeconómicos
                           ▲
                           │
               Construidos desde la EPH
                           ▲
                           │
             Viviendas ─────┐
                            │
                            ▼
                        Personas
                        
No estamos buscando al estudiante dentro de la EPH. Estamos utilizando la EPH para describir el contexto en el que vive ese estudiante.
