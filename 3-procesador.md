# Limitar uso de procesador
Limitar la cantidad de núcleos de CPU:
```
--cpus=<número de núcleos>
```

Asignar núcleos de CPU específicos:
```
--cpuset-cpus=<lista de núcleos>
```

**¿Como saber el numero de procesadores virtuales que tiene una máquina?**
Para conocer el número de procesadores virtuales en una máquina, puedes utilizar alguno de los siguientes comandos según el sistema operativo:
	
	En Linux (bash)
		lscpu | grep "^CPU(s):" o nproc
	
	En Windows (powershell)
	  Get-WmiObject -Class Win32_Processor | Select-Object -Property NumberOfLogicalProcessors
	
	En macOS (bash)
		sysctl -n hw.logicalcpu
	
	Estos comandos mostrarán la cantidad de procesadores virtuales (o hilos de ejecución) disponibles en tu sistema.

## Ejemplos
_Puedes copiar y ejecutar directamente cada uno de los comandos_

Limitar el uso de CPU a 1.5 núcleos
```
docker run -d --name server-nginx --cpus="1.5" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 0 a 2:
```
docker run -d --name server-nginx --cpuset-cpus="0-2" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 1 y 3:
```
docker run -d --name server-nginx --cpuset-cpus="1,3" nginx:alpine
```
