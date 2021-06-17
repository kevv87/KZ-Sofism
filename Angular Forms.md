# Angular Forms
Hay dos maneras de trabajar con los formularios que Angular da:

## Template-driven
En general estos son más sencillo y más fáciles de implementar.

Un ejemplo funcional de un template driven form es el siguiente:
```
<form (ngSubmit)="onSubmit()" #studentForm\="ngForm">

<mat-form-field\>

<mat-label\>Correo del nuevo estudiante</mat-label\>

<input name\="mail" \[(ngModel)\]="model.mail"

  type\="text" required #mail\="ngModel"

  matInput placeholder\="example@mail.com"

\>

</mat-form-field\>

<button mat-button type\="submit"     [disabled\]="!studentForm.form.valid"\>Agregar</button\>

</form\>
```

Aquí se notan ciertos aspectos propios de esta manera de hacer forms:
- `#studentForm=ngForm` Hay que ponerle un nombre al form e igualarlo a ngForm
- `[(ngModel)]="model.mail"` Este es el valor en el .ts al que va a ser igual este campo del form
- `#mail="ngModel"`: Hay que darle también un nombre a cada campo del form e igualarlo a ngModel

## Reactive
En general estos son más complejos, pero mejores.