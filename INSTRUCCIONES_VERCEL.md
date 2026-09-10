# Instrucciones para Configurar Focus TDH en Vercel con Supabase

## Paso 1: Configurar Base de Datos en Supabase

1. Ingresa a tu proyecto de Supabase: https://supabase.com/dashboard
2. Ve a la sección **SQL Editor**
3. Ejecuta el contenido del archivo `db_schema.txt` para crear todas las tablas necesarias
4. El script creará:
   - Tabla `perfiles_usuarios` (con campo docente_id)
   - Tabla `sesiones_entrenamiento`
   - Tabla `metricas_minijuegos`
   - Tabla `evaluaciones_docente`
   - Triggers automáticos para crear perfiles y sesiones
   - Políticas de seguridad (RLS)

## Paso 2: Configurar Variables de Entorno en Vercel

1. En tu proyecto de Vercel, ve a **Settings > Environment Variables**
2. Agrega las siguientes variables:

```
VITE_SUPABASE_URL=https://qxoxcloiaxdwkpdizfzk.supabase.co
VITE_SUPABASE_ANON_KEY=sb_publishable_yjd-kkUdxurJwbAZcx-XQA_TzzraUc-
```

3. Haz clic en **Save** y luego **Redeploy** tu proyecto

## Paso 3: Verificar que Funciona

Una vez desplegado:

1. Abre tu aplicación en Vercel
2. Regístrate como estudiante (selecciona un profesor)
3. Regístrate como docente
4. Los datos se guardarán en Supabase (base de datos en la nube)
5. Podrás acceder desde cualquier dispositivo y ver los mismos datos

## ¿Cómo funciona ahora?

- **Antes**: Los datos se guardaban en `localStorage` (solo en el navegador de cada dispositivo)
- **Ahora**: Los datos se guardan en Supabase (base de datos en la nube)
- **Resultado**: Si un estudiante juega en un celular, cuando entre desde otro celular verá su progreso
- **Profesores**: Podrán ver el progreso de sus estudiantes desde cualquier dispositivo

## Solución de Problemas

Si no carga Supabase:

1. Verifica que las variables de entorno estén correctamente configuradas en Vercel
2. Abre la consola del navegador (F12) y busca errores de conexión
3. Asegúrate de que el script SQL se ejecutó correctamente en Supabase

## Notas Importantes

- Los datos ya existentes en localStorage no se migran automáticamente a Supabase
- Los nuevos registros y actividades se guardarán en Supabase
- Para mantener los datos existentes, necesitarías crear un script de migración
