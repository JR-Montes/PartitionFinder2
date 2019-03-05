## Tutorial PartitionFinder2

Cognato AI, Vogler AP. Exploring data interaction and nucleotide alignment in a multiple gene analysis of Ips (Coleoptera: Scolytinae). Systematic Biology. 2001 Nov 1;50(6):758-80.
 
____


Este tutorial proporciona los requisitos y el procedimiento para correr un análisis en `PartitionFinder`y encontrar el mejor esquema de particiones en un alineamiento. `PartitionFinder2`permite comparar esquemas de partición para alineamientos de secuencias de ADN. Este tutorial puede ayudar si no estás seguro acerca de algún aspecto en particular de su análisis, o si nunca ha pensado en particionar esquemas antes. Para más información viste el manual de `PartitionFinder2` (en la carpeta 'documentos' cuando descargue PartitionFinder). Para los fines de este tutorial, asumiré que está usando una Mac. Para análisis en Windows deberá modificar ligeramente la sección 4; los detalles se encuentran en el manual.

Ahora bien, `PartitionFinder2"` necesita que instalen la distribución [ANACONDA](https://www.anaconda.com/download/) de Python, en su versión 2.7 (NO instalen la 3.6). Utiliza el Graphical Installer 



Primero debe descargar [PartitionFinder2](http://www.robertlanfear.com/partitionfinder/)



**Los archivos que necesitas son:**
| Archivos | inputs |  
| ------   | ------ |
|**i.** Matriz molecular   |(secuencias.phy)| 
|**ii.** Archivo de particiones molecular  | (particion_adn.cfg)|

___

Una vez que descargaste `PartitionFinder2`y `anaconda` podemos comenzar a correr el análisis.

Antes comenzar en necesario que tanto el alineamiento y el esquema de partición se encuentren en la misma carpeta que el programa `PartitionFinder`. En este sentido genera un carpeta llamada "turorial" y ahí coloca los dos archivos. 


**1.** Entra a la terminal de tu computadora:

/Applications/Utilities/folder

**2** Ve a directorio donde tienes `PartitionFinder2`

**3** Escribe la siguiente línea de comandos:

`python PartitionFinder.py tutorial`


En la pantalla se va a imprimir lo siguiente. Esto indica que el programa está corriendo con éxito. Si el programa temrinamuy pronto y no ve lo siguiente entonces debes revisar donde hay errores.

```

INFO | 2016-12-02 18:52:18,186 | ------------- PartitionFinder 2.1.0 -----------------
INFO | 2016-12-02 18:52:18,186 | You have Python version 2.7
INFO | 2016-12-02 18:52:18,186 | Command-line arguments used: /Applications/partitionfinder-2.1.0/PartitionFinder.py /Users/robertlanfear/Desktop/beetles
INFO | 2016-12-02 18:52:18,186 | ------------- Configuring Parameters -------------
INFO | 2016-12-02 18:52:18,187 | Setting datatype to 'DNA'
INFO | 2016-12-02 18:52:18,187 | Setting phylogeny program to 'phyml'
INFO | 2016-12-02 18:52:18,187 | Program path is here /Applications/partitionfinder-2.1.0/programs
INFO | 2016-12-02 18:52:18,188 | Setting working folder to: '/Users/robertlanfear/Desktop/beetles'
INFO | 2016-12-02 18:52:18,188 | Loading configuration at './partition_finder.cfg'
INFO | 2016-12-02 18:52:18,197 | Setting 'alignment' to 'cognato.phy'
INFO | 2016-12-02 18:52:18,198 | Setting 'branchlengths' to 'linked'
INFO | 2016-12-02 18:52:18,199 | You set 'models' to: GTR, GTR+G, GTR+I+G
INFO | 2016-12-02 18:52:18,215 | This analysis will use the following 3 models of molecular evolution
INFO | 2016-12-02 18:52:18,216 | GTR, GTR+G, GTR+I+G
INFO | 2016-12-02 18:52:18,217 | Setting 'model_selection' to 'aicc'
INFO | 2016-12-02 18:52:18,230 | Setting 'search' to 'greedy'
INFO | 2016-12-02 18:52:18,230 | ------------------------ BEGINNING NEW RUN -------------------------------
INFO | 2016-12-02 18:52:18,231 | Looking for alignment file './cognato.phy'...
INFO | 2016-12-02 18:52:18,238 | Using 4 cpus
INFO | 2016-12-02 18:52:18,238 | Beginning Analysis
INFO | 2016-12-02 18:52:18,263 | Reading alignment file './cognato.phy'
INFO | 2016-12-02 18:52:18,276 | Starting tree will be estimated from the data.
INFO | 2016-12-02 18:52:18,277 | Estimating Maximum Likelihood tree with RAxML fast experimental tree search for ./analysis/start_tree/filtered_source.phy
INFO | 2016-12-02 18:52:18,278 | Using a separate GTR+G model for each data block
INFO | 2016-12-02 18:52:45,662 | ML topology estimation finished
INFO | 2016-12-02 18:52:45,663 | Performing Greedy Analysis
INFO | 2016-12-02 18:52:45,664 | *** Analysing starting scheme ***
INFO | 2016-12-02 18:52:50,057 | Finished subset 1/7, 14.29 percent done
INFO | 2016-12-02 18:52:57,972 | Finished subset 2/7, 28.57 percent done
INFO | 2016-12-02 18:52:59,855 | Finished subset 3/7, 42.86 percent done
INFO | 2016-12-02 18:53:00,728 | Finished subset 4/7, 57.14 percent done
INFO | 2016-12-02 18:53:06,518 | Finished subset 5/7, 71.43 percent done
INFO | 2016-12-02 18:53:07,658 | Finished subset 6/7, 85.71 percent done
INFO | 2016-12-02 18:53:14,037 | Finished subset 7/7, 100.00 percent done
INFO | 2016-12-02 18:53:14,038 | ***Greedy algorithm step 1***
INFO | 2016-12-02 18:53:14,039 | Analysing 21 new subset pairs
INFO | 2016-12-02 18:53:24,687 | Finished subset 1/21, 4.76 percent done

```

**4** Interpretar los resultados.

Una vez que `PartitionFinder2` haya terminado, los resultados se almacenarán en la carpeta /analysis. Aquí hay mucha información almacenada, las descripciones de todo esto se pueden encontrar al final del manual PartitionFinder2. El resultado principal está en el archivo `best_scheme.txt`. Si abre ese archivo, observará que comienza describiendo la configuración utilizada para la ejecución. Debajo de eso, debería ver algo como esto (note that results may differ slightly on different systems, because PhyML works a little different on Linux, Mac and Windows):


```
Best partitioning scheme

Scheme Name       : step_1
Scheme lnL        : -18431.2988281
Scheme AICc       : 37183.8287775
Number of params  : 148
Number of sites   : 1897
Number of subsets : 6

Subset | Best Model | # sites    | subset id                        | Partition names                                                                                     
1      | GTR+I+G    | 217        | d382a6be22e2495575e4d97003dcc693 | ef1a_1stpos                                                                                         
2      | GTR+I+G    | 471        | 1638e275adde7fea81f6d7e3ba7b4d49 | ef1a_2ndpos, COI_2ndpos                                                                             
3      | GTR+G      | 216        | d6496c25c9e9550070851560ef7d9b29 | ef1a_3rdpos                                                                                         
4      | GTR+I+G    | 256        | a51426084bd4082ec2c2c49b88ac4628 | COI_1stpos                                                                                          
5      | GTR+G      | 255        | 0195ef30a620e50b9307a2be784bf230 | COI_3rdpos                                                                                          
6      | GTR+I+G    | 482        | 7b895a8ce777707287ca690df280b5dd | 16S    

```   

Las primeras líneas le brindan información general sobre este esquema de partición. La información útil está en la tabla debajo de esas líneas. Cada fila en esta tabla le informa acerca de un subconjunto del mejor esquema de partición. Primero, esta tabla muestra que el esquema de partición de mejor ajuste encontrado por el algoritmo codicioso tiene 6 subconjuntos. En este análisis, el mejor esquema simplemente combina dos de los bloques de datos originales que corresponden a las posiciones del segundo codón de los genes codificantes de proteínas. Esto parece sensato, ya que sabemos que las posiciones del segundo codón tienden a evolucionar mucho más lentamente que otras posiciones del codón.

El archivo de salida también le informa los resultados de la selección del modelo en cada uno de los subconjuntos. Por ejemplo, la primera fila le indica que para la partición formada por la primera posición de codón de ef1a, el modelo de sustitución de mejor ajuste según el AICc fue el modelo GTR + I + G. Esta información le indica todo lo que necesita para seguir adelante y usar este conjunto de datos para un análisis filogenético particionado, por ejemplo, utilizando Garli, BEAST o MrBayes. Para ayudarlo con los análisis posteriores, notará que más abajo en el archivo, el esquema de partición está escrito en un rango de formatos adecuados para diferentes programas.

Si desea más detalles sobre la selección del modelo para un subconjunto en particular, puede obtenerlo muy fácilmente. Para obtener más información sobre los resultados de la selección del modelo para un subconjunto en particular, solo obtenga el nombre de ese subconjunto de la columna `'nombre'` `"best_scheme.txt"` (que se muestra arriba), luego busque un archivo con ese nombre en la carpeta análisis / subconjuntos / . Este archivo contiene información sobre cada uno de los modelos analizados para ese subconjunto, ordenados según su puntuación AICc.

Aquí están las primeras líneas del archivo de selección de modelo que corresponde al primer subconjunto en el análisis anterior (tenga en cuenta que puede haber pequeñas diferencias en los resultados entre los sistemas operativos, debido a la forma en que PhyML funciona en diferentes máquinas):

```
Model selection results for subset: d382a6be22e2495575e4d97003dcc693
Subset alignment stored here: ./analysis/phylofiles/d382a6be22e2495575e4d97003dcc693.phy
This subset contains the following data_blocks: ef1a_1stpos
Number of columns in subset: 217
Models are organised according to their AICc scores

Model           | Parameters      | lnL             | AICc             | AIC             | BIC            
GTR+I+G         | 10              | -708.347        | 1437.76          | 1436.69         | 1470.49        
GTR+G           | 9               | -730.689        | 1480.25          | 1479.38         | 1509.8         
GTR             | 8               | -808.053        | 1632.8           | 1632.11         | 1659.15        

```

Estos resultados muestran que el modelo GTR + I + G es bastante mejor que los otros dos modelos en este subconjunto de sitios.


`PartitionFinder2` le proporciona toda la información necesaria para realizar un análisis filogenético particionado, por ejemplo. en `RaxML`, `BEAST`, `MrBayes`, o `Garli`. No es necesario realizar más comparaciones de modelos ni de esquemas de partición después de ejecutar `PartitionFinder2`. Si está utilizando un programa (como `RaxML` o `MrBayes 3.1.2`) que no implementa todos los 56 modelos de sustitución, `PartitionFinder2` incluye un par de opciones adicionales que pueden ser útiles. Por ejemplo, hay varias listas de modelos predefinidas, que se describen en el manual. Esto puede evitar que escribas largas listas de modelos. También tenga en cuenta que si cambia la lista de modelos para un análisis, PF2 reutilizará los resultados anteriores que tenga, por lo que puede ser muy rápido. Por ejemplo, si incluye un modelo adicional (por ejemplo, `JC + I + G`) en la lista en el archivo de configuración, y vuelve a ejecutar su análisis, será más rápido que la última vez.
`PartitionFinder2` también incluye la opción de usar RAxML para la comparación de todos los modelos y esquemas de partición (que es mucho más rápido que PhyML), y también incluye dos nuevos algoritmos de búsqueda (hcluster y rcluster) para encontrar esquemas de partición en conjuntos de datos muy grandes.

Aquí hay algunas sugerencias de análisis que puede probar a continuación, para tener una idea de cómo funciona `PartitionFinder2`:
Intente ejecutar `PartitionFinder2` con un conjunto de modelos más pequeño (por ejemplo, `"modelos = GTR + G;"`). Notará que se ejecuta muy rápido, eso es porque ha almacenado todos los resultados del análisis anterior y los está utilizando.
Intente ejecutar `PartitionFinder2` con la opción de línea de comandos `"--raxml"`. Si ha estado siguiendo este tutorial, notará que esto le da un error, porque `PartitionFinder2` no puede reutilizar los datos de las ejecuciones anteriores (en las que se utilizó PhyML para calcular las probabilidades), por lo que se cierra sin hacer nada. cualquier cosa. Esto es para asegurarse de que no sobrescriba accidentalmente sus análisis anteriores. Siga las instrucciones del mensaje de error y agregue la opción `"--force-restart"`. Eso hará que `PartitionFinder2` elimine todos los resultados almacenados y comience de nuevo. Este análisis será más rápido que el análisis PhyML (incluso con los mismos tres modelos GTR analizados desde cero) porque RAxML es más rápido que PhyML.
Intente cambiar la opción de búsqueda a `"search = rcluster;"` y ejecutándolo de nuevo. Esto implementa un método rápido de agrupación en clústeres para buscar esquemas de partición. Puede obtener un resultado ligeramente diferente. En general, solo debe usar esta opción cuando `"search = greedy;"` La opción es demasiado lenta para su conjunto de datos.