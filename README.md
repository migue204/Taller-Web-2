# Taller-Web-2

CRUD de las Series de Televisión
 Es una app donde puedes ver, buscar, crear, editar y eliminar series de televisión, y marcarlas como favoritas. Los datos se guardan en el navegador (localStorage), así que no se pierden al recargar la página.
Tecnologías que se usaron
 Next.js (App Router)
- TypeScript
- React
- Tailwind CSS
Cómo instalar y correr el proyecto
1. Clona el repositorio:
   git clone <URL-de-tu-repositorio>
   cd crud-series-isis3710
2. Instala las dependencias:
   npm install
3. Corre el proyecto en modo desarrollo:
   npm run dev
4. Abre el local host en el navegador.
Estructura del proyecto
app/
  layout.tsx -> Layout general de la app (Server Component)
  page.tsx    -> Página principal, muestra la lista de series
  nueva/page.tsx     -> Página para crear una serie nueva
  series/[id]/page.sx-> Página de detalle de una serie
  series/[id]/editar/page.tsx -> Página para editar una serie

components/
  ListaSeries.tsx   -> Lista + búsqueda de series (Client Component)
  SerieCard.tsx   -> Tarjeta de una serie individual
  BarraBusqueda.tsx  -> Input de búsqueda
  CargandoLista.tsx   -> Skeleton mientras cargan los datos
  FormularioSerie.tsx -> Formulario reutilizado para crear y editar
  DetalleSerie.tsx  -> Vista de detalle, con eliminar y confirmación

lib/
  types.ts        -> Definición del tipo Serie
  storage.ts  -> Funciones para leer/guardar en localStorage
  useSeries.ts -> Hook que centraliza la carga y guardado de series
Funcionalidades
Ver lista de series con nombre, género, año, temporadas y estado.
Buscar series por nombre en tiempo real.
Crear una serie nueva con formulario validado.
Ver el detalle completo de una serie.
Editar una serie existente (formulario pre-llenado).
Eliminar una serie, con un cuadro de confirmación antes de borrar.
Marcar/desmarcar series como favoritas.
Los datos persisten en el navegador usando localStorage.
Mensajes de error si algo falla al leer o guardar los datos.
Estado de carga (skeleton) mientras se leen los datos guardados.
Diseño responsive (se ve bien en celular y en computador).

Decisiones de diseño

- Las páginas (page.tsx) son Server Components. La parte interactiva (formularios, favoritos, búsqueda) vive en componentes separados marcados con "use client", siguiendo la recomendación del taller de usar "use client" solo donde de verdad se necesita.
- Se usa un solo componente FormularioSerie para crear y editar, cambiando su comportamiento según la prop modo, en vez de duplicar el formulario dos veces.
- El acceso a localStorage está aislado en lib/storage.ts y siempre revisa que window exista antes de usarlo, para no romper el renderizado en el servidor.
