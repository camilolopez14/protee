<! DOCTYPE html >
< html  lang = " en " >
< cabeza >
	< meta  charset = " utf-8 " >
	< meta  name = " description " content = "" >
	< meta  name = " author " content = "" >
	< meta  name = " viewport " content = " ancho = ancho del dispositivo, escala inicial = 1.0, escalable por el usuario = no " >
	< título > Potree Viewer </ título >

	< link  rel = " stylesheet " type = " text / css " href = " ../build / potree / potree.css " >
	< link  rel = " stylesheet " type = " text / css " href = " ../libs / jquery - ui / jquery - ui.min.css " >
	< link  rel = " stylesheet " type = " text / css " href = " ../libs / perfect - scrollbar /css/ perfect - scrollbar.css " >
	< link  rel = " stylesheet " type = " text / css " href = " ../libs / openlayers3 / ol.css " >
	< link  rel = " stylesheet " type = " text / css " href = " ../libs / spectrum / spectrum.css " >
	< link  rel = " stylesheet " type = " text / css " href = " ../libs / jstree / themes / mixed / style.css " >
</ cabeza >

< cuerpo >
	< script  src = " ../libs / jquery / jquery - 3.1.1.min.js " > </ script >
	< script  src = " ../libs / spectrum / spectrum.js " > </ script >
	< script  src = " ../libs / perfect - scrollbar / js / perfect - scrollbar.jquery.js " > </ script >
	< script  src = " ../libs / jquery - ui / jquery - ui.min.js " > </ script >
	< script  src = " ../libs / three.js / build / three.min.js " > </ script >
	< script  src = " ../libs / other / BinaryHeap.js " > </ script >
	< script  src = " ../libs / tween / tween.min.js " > </ script >
	< script  src = " ../libs / d3 / d3.js " > </ script >
	< script  src = " ../libs / proj4 / proj4.js " > </ script >
	< script  src = " ../libs / openlayers3 / ol.js " > </ script >
	< script  src = " ../libs / i18next / i18next.js " > </ script >
	< script  src = " ../libs / jstree / jstree.js " > </ script >
	< script  src = " ../build / potree / potree.js " > </ script >
	< script  src = " ../libs / plasio / js / laslaz.js " > </ script >
	
	<! - INCLUYE DEPENDENCIAS ADICIONALES AQUÍ ->
	<! - INCLUYE AJUSTES AQUÍ ->
	
	< div  class = " potree_container " style = " position: absolute; width: 100%; height: 100%; left: 0px; top: 0px; " >
		< div  id = " potree_render_area " > </ div >
		< div  id = " potree_sidebar_container " >  </ div >
	</ div >
	
	< guión >
	
		ventana . espectador  =  nuevo  Potree . Visor ( documento . GetElementById ( "potree_render_area" ) ) ;
		
		espectador . setEDLEnabled ( verdadero ) ;
		espectador . setDescription ( "Agregar una sección personalizada a la barra lateral" ) ;
		
		espectador . loadGUI ( ( )  =>  {
			espectador . toggleSidebar ( ) ;
			
			let  section  =  $ ( `
				<h3 id = "menu_meta" class = "accordion-header ui-widget"> <span> Metadatos </span> </h3>
				<div class = "accordion-content ui-widget pv-menu-list"> </div>
			` ) ;
			dejar  contenido  =  sección . last ( ) ;
			contenido . html ( `
			<div class = "pv-menu-list">
				¡Una sección personalizada en la barra lateral! <br>
				<br>	
				Descomenta "content.hide ();" para ocultar contenido por defecto. <br>
				<br>
				Eche un vistazo a src / viewer / sidebar.html y sidebar.js para 
				Aprenda cómo se rellenaron las otras secciones.
			</div>
			` ) ;
			sección . primero ( ) . haga clic en ( ( )  =>  contenido . slideToggle ( ) ) ;
			sección . insertBefore ( $ ( '#menu_about' ) ) ;
			
		} ) ;
		
		Potree . loadPointCloud ( "../pointclouds/vol_total/cloud.js" ,  "Sorvilier" ,  e  =>  {
			espectador . escena . addPointCloud ( e . nube de puntos ) ;
			espectador . fitToScreen ( ) ;
		} ) ;
		
	</ script >
	
	
  </ cuerpo >
</ html >
