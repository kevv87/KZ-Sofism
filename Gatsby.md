## Info
Librería de [[React]] para crear páginas web estáticas y rápidas.

## Node APIs
Son funciones del API que Gatsby expone, entre otras cosas se usan para: crear páginas dinámicamente, agergar datos a GraphQL o responder a eventos durante el build lifecycle.
Más info: https://www.gatsbyjs.com/docs/reference/config-files/gatsby-node/

### onCreateNode
Esta función se ejecuta cada vez que se crea un nodo.

### createPages
Esta función nos sirve para crear páginas dinámicamente, por ejemplo, a partir de archivos o algún otro recurso.

## Dynamic Data
No es óptimo crear el contenido de una página en vscode, ni tampoco un cliente va a querer hacerlo así, en esta área Gatsby reluce de manera que puede traer el contenido dinámico de fuentes como: Wordpress, Contenful, bases de datos propias, archivos Markdown, entre muchos otros.

Gatsby tiene incluido un servidor de [[GraphQL]] para acceder a él se hace por la url `/___graphql`

### Para datos internos (Como la metadata del sitio)
Estos son datos que vienen de dentro de la página, como la metadata del sitio, se pueden obtener mediante queries simples.


### Para datos externos 
Estos son datos que vienen de afuera de la página, se requieren plugins especificos para cada tipo de fuente de datos

#### Para filesystem
Primero se usa un plugin para acceder al file system, la configuración se ve así:
```
{
      resolve: 'gatsby-source-filesystem',
      options:{
        name:'source',
        path: `${__dirname}/src/`
      }
}
```

Y un query de prueba:
```
query{
  allFile{
    edges{
      node{
        name
        extension
        dir
      }
    }
  }
}
```

#### Para markdowns
Se usa el plugin Remark, con config: `gatsby-transformer-remark`
Ejemplo de query:
```
query{
  allMarkdownRemark{
    edges{
      node{
        frontmatter{
          title
          date
        }
        html
        excerpt
      }
    }
  }
}
```


## Useful notes
- Se usa `Link` para redirigir de manera optimizada dentro de la misma página
	- `<Link to="/page"></Link>`

## Useful commands
- Para crear un nuevo sitio: `gatsby new`
- Correr el sitio: `npx gatsby develop`

## Styling
Usando [[CSS]] plano, al importar una hoja de estilos dentro de un componente, las reglas definidas en la hoja se aplican no solo al componente, si no **a toda la página donde el componente aparece**, para resolver este problema se usa [[CSS Modules]]


## Plugins
Extienden la funcionalidad de gatsby.
Lista en: https://www.gatsbyjs.com/plugins
### Instalación de cada plugin
Para instalar cada plugin hay que seguir los pasos que vienen en **la página del plugin específico**, muchas veces es necesario instalar otras dependencias del plugin con npm y otras configuraciones. Una vez finalizado, se tiene que declarar el uso del plugin dentro del file `gatsby-config.js` 

## Errors and solutions
### You may need an apropiate header to handle this filetype
Se arregla con el gatsby plugin especifico para el tipo de archivo que quiero importar.

