# Diseño: Sitio web profesional + README mejorado (recarmona)

**Fecha:** 2026-06-25
**Branch:** `feature/profile-site`
**Repo:** `recarmona/recarmona` (repo de perfil de GitHub)

## Objetivo

Presentar el contenido del perfil de GitHub de Reinier Carmona de forma profesional en dos
soportes que comparten el mismo contenido real:

1. Un sitio web estático (GitHub Pages).
2. El `README.md` del perfil, reformateado.

El trabajo se hace en una branch para no afectar el README de `main` mientras tanto.

## Enfoque elegido

**Opción A — Página única estática autocontenida.** Un solo `index.html` con CSS inline,
tema oscuro tipo "cloud/terminal", responsive, sin build step ni dependencias. Se despliega
vía GitHub Pages desde el repo (`https://recarmona.github.io/recarmona/`).

Descartadas: multi-archivo HTML/CSS/JS (overkill para una landing) y generadores estáticos
Jekyll/Hugo (build step y dependencias innecesarias).

## Contenido real (fuente: GitHub público)

- **Perfil:** Senior Linux Administrator · Cloud Engineer · SRE · DevOps Engineer.
- **Proyectos propios (no forks)** a destacar:
  - `template-sops` (HCL, ★2) — plantilla de gestión de secretos con SOPS + Terraform.
  - `bigbang-terraform` (HCL) — infraestructura AWS con Terraform.
  - `bigbang-terraform-ec2` (HCL) — provisión de EC2 con Terraform.
  - `terraform-aws-ec2-linux` — EC2 Linux en AWS con Terraform.
  - `terrraform_onboardvm` (HCL) — onboarding/provisión de VMs.
  - `install-docker` (Shell) — automatización de instalación de Docker.
  - `bigbang` (Shell) — scripting de bootstrap de infraestructura.
- **Intereses (forks):** Kubernetes, DevSecOps, GitOps/Flux, homelab self-hosting, Linux/SRE.
- **Stack** (del README actual): AWS, GCP, Azure, Terraform, Kubernetes, Docker, Ansible,
  Jenkins, GitLab, Git, Linux, Bash, PowerShell, Python, Nginx, Raspberry Pi, Grafana,
  MySQL, MariaDB, WordPress.
- **Contacto:** GitHub (real). LinkedIn y email quedan como placeholders para que el usuario
  los complete (GitHub no los expone públicamente).

## Sitio web — `index.html`

Secciones, de arriba a abajo:

1. **Hero** — avatar (`https://avatars.githubusercontent.com/u/38729607?v=4`), nombre, título,
   subtítulo (la frase de transformación de infraestructura), botones CTA (GitHub, ver proyectos).
2. **About** — intro actual del README, pulida.
3. **Skills** — agrupadas en tarjetas por categoría: Cloud & IaC, Contenedores & Orquestación,
   CI/CD & Automatización, OS/Scripting & Servicios, Observabilidad & Datos. Badges por tecnología
   (se usan los mismos assets de iconos del README, o badges de texto si fallan los remotos).
4. **Featured Projects** — grid de tarjetas con los repos propios listados arriba: nombre,
   descripción, lenguaje, enlace al repo.
5. **GitHub Activity** — embeds de `github-readme-stats` (stats + top-langs) y
   `github-profile-trophy`, más el contador de visitas.
6. **Contact** — GitHub (real) + placeholders de LinkedIn/email.
7. **Footer** — copyright y nota "Built with ❤️".

### Decisiones técnicas

- Diseño responsive con CSS Grid/Flexbox; un solo archivo, CSS en `<style>` dentro de `<head>`.
- Tema oscuro (paleta tipo terminal: fondo oscuro, acentos cian/verde). Tipografía del sistema +
  monoespaciada para acentos.
- Imágenes remotas (avatar, badges de stats) cargadas por URL; degradan de forma elegante si no
  cargan. Sin JS obligatorio; scroll suave opcional con CSS.
- Accesibilidad básica: `alt` en imágenes, contraste suficiente, navegación por anclas.

## README.md del perfil

Mismo contenido real, reorganizado:

- Quitar el texto instructivo de plantilla ("Recruiters want to see...", "Adapt to your actual
  achievement", etc.).
- Reemplazar los proyectos genéricos por los repos reales con enlaces.
- Mantener stack, GitHub stats, trophies y contador.
- Sección de contacto limpia: GitHub real + placeholders claros de LinkedIn/email.
- Añadir un enlace al sitio web publicado.

## Despliegue (GitHub Pages)

- El sitio se sirve desde el repo. Como es la branch de trabajo, se documentará al usuario que
  para publicar debe activar Pages apuntando a esta branch (o hacer merge a `main` y servir desde
  ahí). No se ejecuta ningún cambio de configuración remota automáticamente.

## Fuera de alcance (YAGNI)

- Backend, formularios de contacto funcionales, analítica propia.
- Generadores estáticos, bundlers, frameworks JS.
- i18n / multi-idioma.
- Modo claro/oscuro conmutable (solo oscuro).

## Criterios de éxito

- `index.html` abre en local y se ve profesional y responsive (móvil + escritorio).
- Todos los enlaces de proyectos apuntan a repos reales existentes.
- README sin placeholders de plantilla genéricos ni texto instructivo.
- `main` queda intacta hasta que el usuario decida hacer merge.
