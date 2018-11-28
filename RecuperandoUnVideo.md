# Recuperando un archivo MP4

El otro día estaba filmando un video en mi teléfono "inteligente", y al finalizar la cámara se colgó, lo que causó que el video no se guardara correctamente. Sin embargo, el archivo del video quedó allí, en el aparato pesando unos 270Mb.

El video estaba allí, y por su tamaño, se suponía que la información estaba allí también, pero el video no se reproducia en ninguna de las aplicaciones que tenía el telefono.

Lo llevé a mi computador con _Linux Fedora_ y tampoco lo logré reproducir. Aquí logré un avance al conseguir que el `ffmpeg` (y `ffplay`, `ffprobe`) me dieran más información de lo ocurrido.

El error en cuestión era:

```[mov,mp4,m4a,3gp,3g2,mj2 @ ] moov atom not found0/0  Invalid data found when processing input```

Esto quiere decir que, al colgarse la aplicación, no se escribió la _tabla de contenido del video_.

Luego de una búsqueda por Google, y toparme con varias aplicaciones _payware_ para Window$ que promenten resolver el problema, conseguí el siguiente link:

https://superuser.com/questions/1033251/how-to-recover-1-4gb-video-file-that-cant-be-read-canon

Que me llevó a este otro link:

https://superuser.com/questions/417100/how-to-open-and-repair-an-m4v-or-mp4-video-file

Que, por último ;-) me llevó a la herramienta *Software Libre* que estaba buscando y que reparó el video:

[Untrunk](http://vcg.isti.cnr.it/~ponchio/untrunc.php)

**Untrunk** es una herramienta que permite reconstruir el `moov atom` de un video a partir de un video similar que no esté dañado.

El video similar debe ser un video de la misma cámara, a la misma resolución, a la misma frecuencia de cuadros.

En la página principal del programa (más arriba) explica, a grosso modo, como funciona. En el [repostorio](https://github.com/ponchio/untrunc) en Github explica como instalarlo y usarlo. Las instrucciones están claras y explica diferentes opciones de uso, incluyendo una distribución Docker, ya que usa una versión de bibliotecas de libav bastante viejas.

Yo use la segunda opción, bajar las bibliotecas y compilarlas. Probablemente la versión Docker hubiese funcionado bien también.

Espero que les sea útil esta información.

RAG
