# Deploy de la calculadora de costos

Objetivo: que una persona pueda usar la calculadora desde una URL sin instalar Node, clonar el repo ni levantar la API local.

## Modo recomendado inicial

Publicar el frontend `apps/web` y usar la calculadora con almacenamiento local del navegador:

- los Excel se procesan en el navegador
- parametros, reglas y ultimos archivos quedan en `localStorage`
- no se necesita backend para calcular
- la configuracion se puede mover entre maquinas con "Generar configuracion" e "Importar configuracion"

Variable sugerida:

```bash
NEXT_PUBLIC_COSTS_CONFIG_MODE=local
```

URL para compartir:

```text
/reportes/costos
```

## Deploy sugerido en Vercel

1. Conectar el repo `santiachar-ai/ERP`.
2. Configurar el proyecto con root directory `apps/web`.
3. Build command: `npm run build`.
4. Output: Next.js automatico.
5. Agregar variable `NEXT_PUBLIC_COSTS_CONFIG_MODE=local`.
6. Deployar y compartir la URL `/reportes/costos`.

## Limitaciones del modo local

- Cada usuario conserva sus reglas y archivos en su propio navegador.
- Si borra datos del navegador, pierde archivos y parametros locales.
- No hay configuracion central compartida.
- No hay usuarios ni permisos.

## Siguiente etapa

Para una version multiusuario:

1. Publicar la API.
2. Usar base de datos cloud.
3. Agregar login.
4. Guardar configuraciones por empresa o usuario.
5. Agregar plantillas de archivos esperados y validacion con mensajes mas guiados.
