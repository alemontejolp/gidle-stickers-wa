# Contribución a (G)I-DLE Stickers

Debido a que esta aplicación no está pensada para servir de algo más que
como un repositorio de stickers de (G)I-DLE, no se esperan cambios
significativos en el código fuente, sino más bien en los paquetes
de stickers disponibles, que normalmente deberían aumentar.

En otras palabras, la contribución consiste en crear más paquetes de
stickers.

Antes de enviar una contribución, por favor asegurese de que los
stickers que propone para ser agregados no se repiten, es decir,
no están ya en la aplicación.

## Paquetes de stickers

Los paquetes de stickers son directorios con al menos 3 y como máximo
30 imágenes de 512x512 pixeles en formato WebP, las cuales serán los
stickers, y una imágen de 96x96 pixeles en formato png, que será el
ícono que se mostrará en la bandeja de stickers de WhatsApp y que
representará al paquete de stickers. Los stickers deben pesar menos
de 100KB y el ícono del pack debe pesar menos de 50KB.

Puede usar [esta herramienta online](https://squoosh.app/) para 
convertir a webp.

Si usa GIMP como editor de imágenes, puede usar las platillas que
se encuentran en el [directorio sticker-templates](sticker-templates/) 
para crear sus stickers e íconos de bandeja.

El ícono que representa el paquete de stickers debe llamarse: **tray_icon.png**.

Los stickers deben ser nombrados con números, desde 1 hasta **n**, siendo **n** la cantidad de stickers que planee agregar, respetando las
restricciones: 3 >= n <= 30. Por ejemplo: 1.webp, 2.webp, ... n.webp.

Aunque el mínimo de stickers es 3, es muy recomendable que cree al menos
25 de ellos para no agregar paquetes demaciado pequeños. 

Los paquetes de stickers deben ser por cada miembro, o en grupo. 
Esto significa que cada paquete de stickers sólo debe contener stickers
de una sola miembro, o bien contener stickers en dónde en cada uno haya más de una miembro.

A los paquetes de stickers en donde en cada sticker aparece más de una miebro les llamamos **gidle**, y si los stickers son de una sola miebro,
son nombrados por el nombre de la miebro.

## Cómo agregar los paquetes de stickers a la app.

Hay dos formas en las que se puede hacer esa contribución.

Creando los paquetes de stickers y...

1. enviandolos a mi email para que yo los agregué posteriormente a la app.
2. agregandolos directamente a la app, en el directorio correspondiente, y registrandolos en el archivo que sirve de base de datos de stickers.

### 1. Enviando los paquetes de stickers a mi email

Si decidió la primera opción, puede escribirme a: alemontejo.lp@gmail.com
mencionando que es para agregar nuevos paquetes de stickers, adjuntando
los paquetes de stickers en un archivo comprimido en zip o rar.

### 2. Haciendo un pull request

Esta opción asume que usted entiende como funciona el formato JSON, 
que sabe usar al menos lo básico de GIT y que tiene conocimientos 
básicos de programación. Si no es el caso, por favor use la opción 1.

#### PASO 1:

Si decidió la segunda opción, deberá hacer un fork de este repositorio y 
crear una nueva rama a partir de master.

Luego deberá copiar sus paquetes de stickers a el siguiente 
directorio: `Android/app/src/main/assets/`. 

Dado que los paquetes de stickers llevan los nombres da las miembros, o bien el nombre **gidle** cuando son stickers grupales, deberá agregar
al final del nombre del paquete lo siguiente **_i**, siendo **i**
el número disponible siguiente. Por ejemplo, si su paquete de stickers es
de Minnie, si hubiera 4 paquetes de stickers de Minnie, el último paquete
de Minnie se llamaría **minnie_4**, entonces el suyo debería llamarse
**minnie_5**.

#### PASO 2:

Registrar los paquetes en la base de datos de stickers, la cual es un
archivo JSON en el mismo directorio del paso 1 llamado **contents.json**.

A continuación se presenta una plantilla para registrar los datos
del paquete de stickers.

```json
    {
      "identifier": "gidle_1",
      "name": "(G)I-DLE 1",
      "publisher": "Ale Montejo Lopez",
      "tray_image_file": "tray_icon.png",
      "image_data_version":"1",
      "avoid_cache":false,
      "publisher_email":"",
      "publisher_website": "",
      "privacy_policy_website": "",
      "license_agreement_website": "",
      "stickers": [
        {
          "image_file": "1.webp",
          "emojis": ["🙂", "♥"]
        },
        {
          "image_file": "2.webp",
          "emojis": ["🙂", "♥"]
        },
        ...
      ]
    }
```

Esta plantilla deberá ser pegada en el lugar correspondiente, dentro de
la propiedad **sticker_packs**, que es un arreglo que contiene el
registro de los paks de stickers. 

Los datos importantes a cambiar son:

* **identifier** : El nombre de la carpeta que contiene sus stickers.
* **name**: El nombre del paquete de stickers que se desplegará en la app.
* **stickers** : Un arreglo de objetos con datos sobre cada sticker del
paquete.

#### PASO 3:

Cuando todo esté listo, puede subir su rama a su fork y hacer un pull
request a este repositorio, a la rama master. Use la plantilla para hacer
PR llamada **Stickers**.
