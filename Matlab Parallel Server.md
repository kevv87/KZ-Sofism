# Matlab Parallel Server
Es una herramienta de [[Matlab]] que se instala en clusters para poder aprovechar los diferentes workers que tienen los clusters al correr programas de Matlab.

Básicamente hay tres agentes que juegan un papel en una configuración de parallel server:
a. Nodo maestro: Aquí se instala el license manager y es donde está instalando el scheduler, como [[Slurm]].
b. Nodos de computación: Cada nodo de computación tiene que tener instalado una copia de Matlab Parallel Server, aquí es donde se van a correr los programas.
c. Cliente: El cliente tiene instalado una copia de Matlab que se conecta con el nodo maestro para programar el trabajo del usuario. Esta copia de Matlab tiene que tener instalado un plugin de slurm para poder conectarse bien con el servidor scheduler.
	- En el caso de clusters con "module load", el cliente de matlab puede ser perfectamente un módulo que se carga.

## Instalación
Su instalación y utilización sigue los siguientes pasos:
1. Instalar el License Manager en el nodo maestro
2. Instalar Matlab Parallel Server en los nodos de cómputo
3. Instalar Matlab en el cliente
4. Configurar el cliente instalando el plugin de slurm correctamente.

Para más pasos: https://www.mathworks.com/help/matlab-parallel-server/install-and-configure-matlab-parallel-server-for-slurm-1.html