# Python-docx-template
Es una librería de Python que extiende la funcionalidad de [[python-docx]], se dice que esta última es muy eficaz creando documentos, pero no modificándolos. 

Esta librería trabaja con el templating language de [[Python Jinja 2]], lo que permite usar toda la sintaxis de dicha librería dentro de los documentos de Word, con unas pocas [restricciones](https://docxtpl.readthedocs.io/en/latest/#restrictions).

A continuación un ejemplo del funcionamiento más simple, reemplazar un texto en un documento:

```python
from docxtpl import DocxTemplate, RichText

tpl = DocxTemplate('./tpl.docx')

context = {
  'date':'01/01/01'
}

tpl.render(context)
tpl.save('./tpl_out.docx')
```

Este código reemplazará todas las ocurrencias de `{{ date }}` en el documento con `'01/01/01'`.

## Reemplazar imágenes
```python
# -*- coding: utf-8 -*-
'''
Created : 2017-09-03

@author: Eric Lapouyade
'''

from docxtpl import DocxTemplate

DEST_FILE = 'output/replace_picture.docx'

tpl = DocxTemplate('templates/replace_picture_tpl.docx')

context = {}

tpl.replace_pic('python_logo.png', 'templates/python.png')
tpl.render(context)
tpl.save(DEST_FILE)
```

Donde se substituye:
- `output/replace_picture.docx` por el path del documento de salida
- `templates/replace_picture_tpl.docx` por el path del documento de entrada
- `python_logo.png` por el **texto alternativo** de la imagen a reemplazar
- `tamplates/python.png` por el path de la imagen de reemplazo

--- 
Volver a [[Python]]