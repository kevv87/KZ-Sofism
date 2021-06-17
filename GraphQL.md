 ## Info
 Una librería para manejo de [[REST Api]]s.
 
 ## Adicionales al request
 ### Search criteria
 Muchas veces hay queries que devuelven únicamente un objeto, si no se les pasa un search criteria estos queries van a devolver únicamente el primer objeto que encuentren.
 
 El search criteria va entre paréntesis y se ve de la siguiente manera:
```
query{
  markdownRemark(
    fields: {
      slug:{
        eq:"gatsby"
      }
    }
  ){
    frontmatter{
      title
    }
  }
}
```
 
 ### Query variables
 Son variables que se le pueden pasar al query, se definen de la siguiente manera:
```
query(
  $slug:String!
)
```
 Luego, dentro del query se puede user `$slug`
 ## Ejemplos
 ### Request 
```
query{
  site{
    siteMetadata{
      title
    }
  }
} 
```