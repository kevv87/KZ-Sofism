# Google maps and React

## Opcion 2
Utilizando @react-google-maps/api

Documentación: https://react-google-maps-api-docs.netlify.app/

## Opcion 1 
Para llevar a cabo esta integración se utiliza el paquete google-map-react.
Al final no me gustó esta librería porque permite poner elementos en el mapa, sí, pero el zoom es terrible.

### Ejemplo de definición del componente
```jsx
const Map = ({location, zoomLevel}) =>{
  return (
    <div className="map">
      <h2 className="map-h2">Come Visit Us At Our Campus</h2>
  
      <div className="google-map">
        <GoogleMapReact
          bootstrapURLKeys={{ key: 'AIzaSyBWvLYk_pYTrthBZcWPL0jVyaQ7EFvfB5A' }}
          defaultCenter={location}
          defaultZoom={zoomLevel}
        >
          <LocationPin
            lat={location.lat}
            lng={location.lng}
            text={location.address}
          />
        </GoogleMapReact>
      </div>
    </div>
  )
};
```

### Si se quiere cambiar el tipo de mapa
Los tipos de mapa los define Google, principalmente son tres: "terrain", "satellite", "hybrid" y "terrain". Para cambiar el tipo de mapa hay que crear lo que los desarrolladores de google llaman un mapa customizado (https://developers.google.com/maps/documentation/javascript/maptypes).
En la librería que se usa este mapa customizado se crea con una función, de la siguiente manera:
```jsx
function createMapOptions(maps) {
  // next props are exposed at maps
  // "Animation", "ControlPosition", "MapTypeControlStyle", "MapTypeId",
  // "NavigationControlStyle", "ScaleControlStyle", "StrokePosition", "SymbolPath", "ZoomControlStyle",
  // "DirectionsStatus", "DirectionsTravelMode", "DirectionsUnitSystem", "DistanceMatrixStatus",
  // "DistanceMatrixElementStatus", "ElevationStatus", "GeocoderLocationType", "GeocoderStatus", "KmlLayerStatus",
  // "MaxZoomStatus", "StreetViewStatus", "TransitMode", "TransitRoutePreference", "TravelMode", "UnitSystem"
  return {
    zoomControlOptions: {
      position: maps.ControlPosition.RIGHT_CENTER,
      style: maps.ZoomControlStyle.SMALL
    },
    mapTypeControlOptions: {
      position: maps.ControlPosition.TOP_RIGHT,
    },
    mapTypeId:"terrain"
  };
}
```
Donde si se quiere cambiar especificamente el tipo de mapa, se modifica `mapTypeId`.
Luego, en el componente se le pasa la opción `options=createMapOptions`. Así:
```jsx
<GoogleMapReact
	bootstrapURLKeys={{ 
	  key: 'AIzaSyBWvLYk_pYTrthBZcWPL0jVyaQ7EFvfB5A'
	}}
	defaultCenter={location}
	defaultZoom={zoomLevel}
	options={createMapOptions}
>
```

---
Ir a [[React]]