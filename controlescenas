function nombreLogs(nombreZona)
obj={
  ['Sotano2-Parqueadero']='63/6/1',
  ['Sotano2-Escaleras']='63/6/2',
  ['Sotano2-Ingenieria']='63/6/3',
  ['Sotano1-Parqueadero']='63/6/4',
  ['Sotano1-Exterior']='63/6/5',
  ['Sotano1-Escaleras']='63/6/6',
  ['Sotano1-Lavanderia']='63/6/7',
  ['Piso1-GreatRoom']='63/6/8',
  ['Piso1-GreatBarAndLounge']='63/6/9',
  ['Piso1-BañosGreatRoom']='63/6/10',
  ['Piso1-CoffeeShop']='63/6/11',
  ['Piso1-RumRoom']='63/6/12',
  ['Piso1-WineMclub']='63/6/13',
  ['Piso1-ZonaExterior']='63/6/14',
  ['Piso1-Escaleras']='63/6/15',
  ['Piso1-Management']='63/6/16',
  ['Piso1-ZonaDeEmpleados']='63/6/17',
  ['Piso1-BañosPiscina']='63/6/18',
  ['Piso1-Restaurante']='63/6/19',
  ['Piso1-SalasDeReunion']='63/6/20',
  ['Piso1-PanaderiaAlmacen']='63/6/21',
  ['Piso1-PrepDeComidas']='63/6/22',
  ['Piso1-Basuras']='63/6/23',
  ['Mezzanine-Administracion']='63/6/24',
  ['Mezzanine-BañosAdministrativos']='63/6/25',
  ['Mezzanine-PasilloAZonaEmpleados']='63/6/26',
  ['Mezzanine-ZonaDeEmpleados']='63/6/27',
  ['Mezzanine-Escaleras']='63/6/28',
  ['Mezzanine-Concesiones']='63/6/29',
  ['Mezzanine-PrimerosAuxilios']='63/6/30',
  ['Piso2-Foyer']='63/6/31',
  ['Piso2-BañosFoyer']='63/6/32',
  ['Piso2-SalaDeConferencia1']='63/6/33',
  ['Piso2-SalaDeConferencia2']='63/6/34',
  ['Piso2-SalaDeConferencia3']='63/6/35',
  ['Piso2-SalaDeConferencia4']='63/6/36',
  ['Piso2-SalaDeConferencia5']='63/6/37',
  ['Piso2-SalonesDeEventos']='63/6/38',
  ['Piso2-Escaleras']='63/6/39',
  ['Piso2-Storage']='63/6/40',
  ['Piso2-ZonaServicio']='63/6/41',
  ['Piso3-PasilloPrincipal']='63/6/42',
  ['Piso3-Gimnasio']='63/6/43',
  ['Piso3-Escaleras']='63/6/44',
  ['Piso4-PasilloPrincipal']='63/6/45',
  ['Piso4-Escaleras']='63/6/46',
  ['Piso5-PasilloPrincipal']='63/6/47',
  ['Piso5-Escaleras']='63/6/48',
  ['Piso6-PasilloPrincipal']='63/6/49',
  ['Piso6-Escaleras']='63/6/50',
  ['Piso7-PasilloPrincipal']='63/6/51',
  ['Piso7-Escaleras']='63/6/52',
  ['Piso8-PasilloPrincipal']='63/6/53',
  ['Piso8-Escaleras']='63/6/54',
  ['Piso9-PasilloPrincipal']='63/6/55',
  ['Piso9-Escaleras']='63/6/56',
  ['Piso10-PasilloPrincipal']='63/6/57',
  ['Piso10-Escaleras']='63/6/58',
  ['Piso11-PasilloPrincipal']='63/6/59',
  ['Piso11-Escaleras']='63/6/60'
} 
  dg= obj[nombreZona]
  return dg
end

----------------------------------------FUNCION GUARDAR ESCENA--------------------------------
function guardarEscena(cont, nombre, horaEjecucion, numCtos, arrDim, nombreZona, arrText)
  --[[
  
  --#### ENLAZAR CON BOTONES DE GUARDAR ESCENA 63/1/*####--
  require('user.escenasjose')
  nombre='62/0/1' --Nombre(const)
  horaEjecucion='62/0/2' --hora ejecucion de horario(const)
  --EDIT  
  cont='63/0/x' --contador
  numCtos= ## --numero de ctos
  arrDim={false, true, true, false} -  true ? es dimer: no lo es
  nombreZona='string'
  arrText= {#,{1,2,3,4,5,6,7,8}} --el arrText[1] es la dir intermedia, lo siguiente es el arreglo de la zona
  ]]--
    if (grp.getvalue(cont)<= 8)then
          escena={};
          escena.id=grp.getvalue(cont);
          escena.nombre=grp.getvalue(nombre);
          escena.horaEjecucion=grp.getvalue(horaEjecucion);
          escena.numCtos=numCtos;
          escena.activos={};
          escena.dias={};
    			escena.acc={};
          --//Ctos Escena
          for i = 1, numCtos, 1 do
            if (grp.getvalue('61/0/'..i)) then
              table.insert(escena.activos,i);
              end
            end

          --//Dias Escena
          for i = 1, 7, 1 do
            if (grp.getvalue('62/1/'..i)) then
              table.insert(escena.dias,i);
              end
            end

        --//Ctos Accionamiento
          for index, value in ipairs(escena.activos) do
            if (arrDim[value]) then
              escena.acc[value]=grp.getvalue('61/2/'..value);
            else
              escena.acc[value]=grp.getvalue('61/1/'..value);
            end    
          end


          storage.set(nombreZona..'-'..escena.id, escena);  --GUARDA EN STORAGE
          grp.write(cont, escena.id+1);
    			grp.write('33/'..arrText[1]..'/'..arrText[2][escena.id],escena.id..' - '..escena.nombre); --ESCRIBE EN LISTA
    
            for i=escena.id+1, 8, 1 do
              grp.write('33/'..arrText[1]..'/'..arrText[2][i],'')
            end
    
    grp.write(nombreLogs(nombreZona),"Escena "..escena.id.. " creada");
  else
     grp.write(nombreLogs(nombreZona),'Alcanzo el limite maximo de creacion de escenas')
  end
end
----------------------------------FIN FUNCION GUARDAR ESCENA--------------------------------


------------------- BORRAR SELECTORES DE ESCENA Y CARGAR ESCENA-----------------------------------------------
function borrarConf()
    for i = 1, 17, 1 do
      grp.write('61/0/'..i, false); --RM selector de ctos
      grp.write('61/1/'..i, false); --RM on/off
      grp.write('61/2/'..i, 0); --RM Dimmers
    end
  grp.write('62/0/1', 'No Definido'); -- nombre escena
    for i = 1, 7, 1 do
      grp.write('62/1/'..i, false);
    end
end
--[[
	require('user.escenasjose')
	cont='63/0/x' --contador
  arrDim={false, true, true, false} -- true ? es dimer: no lo es
  nombreZona='string'
	cargarEscena(nombreZona, cont, arrDim)
]]--
function cargarEscena(nombreZona, cont, arrDim)
  borrarConf();
  os.sleep(1);
  id=grp.getvalue('62/0/0');
  
  if(id < grp.getvalue(cont))then
    escena=storage.get(nombreZona..'-'..id);
    	grp.write('62/0/1', escena.nombre); --cargar nombre
    	grp.write('62/0/2', escena.horaEjecucion ); --cargar Hora de ejecucion
    		for index, value in ipairs(escena.dias) do --cargar dias
      		grp.write('62/1/'..value,true);
        end
    		for index, value in ipairs(escena.activos) do --cargar activos
      		grp.write('61/0/'..value,true);
        end

    		for index, value in pairs(escena.acc) do
      		if (arrDim[index]) then
        			grp.write('61/2/'..index, value);
            else
              grp.write('61/1/'..index, value);
            end
        end
   	grp.write(nombreLogs(nombreZona),"Escena "..id.. " Cargada");
  else
    grp.write(nombreLogs(nombreZona),'Escena No Existente');
  end
end
--------------------FIN BORRAR SELECTORES DE ESCENA Y CARGAR ESCENA-------------------------


-----INICIO MODIFICAR ESCENA------------------------
function modificarEscena(cont, nombre, horaEjecucion, numCtos, arrDim, nombreZona, arrText)
  --[[
  
  --#### ENLAZAR CON BOTONES DE GUARDAR ESCENA 63/1/*####--
  require('user.escenasjose')
  nombre='62/0/1' --Nombre(const)
  horaEjecucion='62/0/2' --hora ejecucion de horario(const)
  --EDIT  
  cont='63/0/x' --contador
  numCtos= ## --numero de ctos
  arrDim={false, true, true, false} -  true ? es dimer: no lo es
  nombreZona='string'
  arrText= {#,{1,2,3,4,5,6,7,8}} --el arrText[1] es la dir intermedia, lo siguiente es el arreglo de la zona
  ]]--
  id=grp.getvalue('62/0/0')
  if (id < grp.getvalue(cont))then
    
          escena={};
    			escena.id=id;
          escena.nombre=grp.getvalue(nombre);
          escena.horaEjecucion=grp.getvalue(horaEjecucion);
          escena.numCtos=numCtos;
          escena.activos={};
          escena.dias={};
    			escena.acc={};
          --//Ctos Escena
          for i = 1, numCtos, 1 do
            if (grp.getvalue('61/0/'..i)) then
              table.insert(escena.activos,i);
              end
            end

          --//Dias Escena
          for i = 1, 7, 1 do
            if (grp.getvalue('62/1/'..i)) then
              table.insert(escena.dias,i);
              end
            end

        --//Ctos Accionamiento
          for index, value in ipairs(escena.activos) do
            if (arrDim[value]) then
              escena.acc[value]=grp.getvalue('61/2/'..value);
            else
              escena.acc[value]=grp.getvalue('61/1/'..value);
            end    
          end


          storage.set(nombreZona..'-'..escena.id, escena);  --GUARDA EN STORAGE
    			grp.write('33/'..arrText[1]..'/'..arrText[2][escena.id],escena.id..' - '..escena.nombre); --ESCRIBE EN LISTA
    	grp.write(nombreLogs(nombreZona),"Escena "..escena.id.. " Modificada");
  else
    grp.write(nombreLogs(nombreZona),'Escena No Existente');
  end
end
-----------------------ELIMINAR ESCENA-------------------------------


function eliminarEscena(nombreZona, cont, arrText)
  --[[
  require('user.escenasjose')
  cont='63/0/x' --contador
  nombreZona='string'
  arrText= {#,{1,2,3,4,5,6,7,8}} --el arrText[1] es la dir intermedia, lo siguiente es el arreglo de la zona
  eliminarEscena(nombreZona, cont, arrText)
  ]]--
  borrarConf();
  id=grp.getvalue('62/0/0');
if (id < grp.getvalue(cont))then 
      numAlarmas=grp.getvalue(cont)-1;
      storage.delete(nombreZona..'-'..id);
      os.sleep(1);
      log('Escena '..id..' Eliminada')
      for i=id, numAlarmas-1, 1 do
        escenaNext=storage.get(nombreZona..'-'..i+1);
        escenaNext.id=i;
        storage.set(nombreZona..'-'..i, escenaNext);
        grp.write('33/'..arrText[1]..'/'..arrText[2][i], escenaNext.id..' - '..escenaNext.nombre);
      end

      storage.delete(nombreZona..'-'..numAlarmas);
      grp.write('33/'..arrText[1]..'/'..arrText[2][numAlarmas], '');
      grp.write(cont, numAlarmas);
    grp.write(nombreLogs(nombreZona),'Escena '..id..' Eliminada')
  else
    grp.write(nombreLogs(nombreZona),'Escena No Existente');
  end
end
------------- FIN ELIMINAR ESCENA-----------------------------------

--------------SCHEDULER---------------------------

function matchdate(now, obj)
  function dias(now, obj)
    	for index, value in ipairs(obj.dias) do
          if(now.wday == value) then
            return true;
          end
      end
    return false;
  end
  return type(obj) == 'table' and now.hour == obj.horaEjecucion.hour and now.min == obj.horaEjecucion.minute and dias(now, obj)
end
 
-------------FIN SCHEDULER-------------------------------

-------EJECUTAR ESCENA ----------------------
--[[
  require('user.escenasjose')
  cont='63/0/x' --contador
  nombreZona='string'
	arrDg= {'1/0/1', '1/0/4', '1/0/5', '1/3/2', '1/3/3', '1/3/6', '1/3/7'};
	ejecutarEscena(nombreZona, arrDg, cont)
  ]]--
function ejecutarEscena(nombreZona, arrDg, cont, id)
    
  	if(id == nil)then
      id=grp.getvalue('62/0/0');
    end
  
  	if (id < grp.getvalue(cont))then
  		escena=storage.get(nombreZona..'-'..id);
    
    		for index, value in pairs(escena.acc) do
      			grp.write(arrDg[index], value);
        end
    grp.write(nombreLogs(nombreZona),'Escena '..id..' Ejecutada')
  else
    grp.write(nombreLogs(nombreZona), 'Escena no ejecutada porque no existe')
  end
  
end
-------FIN EJECUTAR ESCENA ----------------------
----------FUNCION SCHEDULER----------------
--[[
  require('user.escenasjose')
  cont='63/0/x' --contador
  nombreZona='string'
	arrDg= {'1/0/1', '1/0/4', '1/0/5', '1/3/2', '1/3/3', '1/3/6', '1/3/7'};
	scheduler(nombreZona, arrDg, cont)
  ]]--
function scheduler(nombreZona, arrDg, cont)
  now = os.date('*t')
  numAlarmas= grp.getvalue(cont)-1;
  for i=1, numAlarmas, 1 do
    escena= storage.get(nombreZona..'-'..i);
    if matchdate(now, escena)then
      log('MATCHDATE')
     ejecutarEscena(nombreZona, arrDg, cont, i)
    end
  end
end  


