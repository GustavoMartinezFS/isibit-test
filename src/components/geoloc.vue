<template>
  <!-- División o secciona para mostrar coordenadas -->
  <div>

    <div id="errores"></div>
		<div id='mapa'></div> 
  </div>
</template>

<script src="http://maps.google.com/maps/api/js?sensor=false"></script>
<script>
export default {
}
		var x=document.getElementById("errores");
			
			navigator.geolocation.getCurrentPosition(mostrarPosicion,showError); //Obtiene la posición
			
			function mostrarPosicion(position)
			{
				var lat=position.coords.latitude; //Obtener latitud
				var lon=position.coords.longitude; //Obtener longitud
				var latlon=new google.maps.LatLng(lat, lon); //Crear objeto que representa un punto geográfico
				divmapa=document.getElementById('mapa');
				divmapa.style.height='600px'; //Alto
				divmapa.style.width='800px'; //Ancho
				
				var myOptions={
					center:latlon,zoom:10, //Zoom
					mapTypeId:google.maps.MapTypeId.ROADMAP, //Tipo de mapa
					mapTypeControl:false, //Deshabilita el control de tipo de mapa
					navigationControlOptions:{ style:google.maps.NavigationControlStyle.SMALL } //Aspecto pequeño
				};
				var map=new google.maps.Map(document.getElementById("mapa"),myOptions); //Funcion que crea un mapa en la div .
				var marker=new google.maps.Marker({position:latlon,map:map,title:"Estás aquí!"}); //Constructor para crear marcador de la posición
			}
			
			function showError(error)
			{
				switch(error.code) 
				{
					case error.PERMISSION_DENIED:
					x.innerHTML="Denegada la peticion de Geolocalización en el navegador."
					break;
					case error.POSITION_UNAVAILABLE:
					x.innerHTML="La información de la localización no esta disponible."
					break;
					case error.TIMEOUT:
					x.innerHTML="El tiempo de petición ha expirado."
					break;
					case error.UNKNOWN_ERROR:
					x.innerHTML="Ha ocurrido un error desconocido."
					break;
				}
			}		

</script>

<style>

</style>