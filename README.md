# Pipeline de Integración/Despliegue Continuo e Infraestructura como Código en AWS

Este proyecto implementa una arquitectura moderna de **CI/CD** (Integración y Despliegue Continuo) e **IaC** (Infraestructura como Código) para desplegar una **página web estática** en **Amazon Web Services (AWS)** utilizando **Terraform** y **GitHub Actions**.

---

## 📁 Estructura del Proyecto

El repositorio está organizado de la siguiente manera, reflejando una separación clara entre el código fuente de la aplicación, la infraestructura y la automatización:

```text
.
├── .github/
│   └── workflows/
│       └── deploy.yml      # Pipeline de GitHub Actions para CI/CD
├── app/
│   ├── index.html          # Código fuente HTML de la web estática
│   └── style.css           # Estilos CSS de la web estática
├── infra/
│   └── main.tf             # Configuración de Terraform para la infraestructura en AWS (S3, etc.)
└── README.md               # Documentación del proyecto
```

---

## 🚀 Arquitectura y Tecnologías

1. **Infraestructura como Código (IaC):** **Terraform** (`infra/main.tf`) se encarga de aprovisionar y gestionar los recursos en AWS de manera declarativa (creación del bucket de S3, políticas de acceso público o configuración de sitio web estático).
2. **Control de Versiones y Automatización (CI/CD):** **GitHub Actions** (`.github/workflows/deploy.yml`) automatiza el flujo de trabajo. Cada vez que se realiza un cambio (push) en la rama principal:
   * Valida o aplica la infraestructura con Terraform (opcionalmente).
   * Sincroniza y despliega automáticamente los archivos estáticos de la carpeta `app/` hacia el bucket S3 en AWS.
3. **Alojamiento Web:** **Amazon S3** almacena y sirve los archivos estáticos (`index.html` y `style.css`) con alta disponibilidad.

---

## ⚙️ Prerrequisitos y Configuración

Para poner en marcha este proyecto en tu propio entorno de AWS y GitHub, asegúrate de cumplir con los siguientes requisitos:

1. **Cuenta de AWS** con permisos para crear buckets S3 y gestionar políticas de acceso.
2. **Credenciales de AWS configuradas en GitHub Secrets:**
   * `AWS_ACCESS_KEY_ID`
   * `AWS_SECRET_ACCESS_KEY`
   * `AWS_REGION` (ej. `us-east-1`)
3. **Terraform CLI** instalado localmente (si deseas probar la infraestructura de forma manual antes de automatizarla).

---

## 🛠️ Despliegue Local (Opcional)

Si deseas aplicar la infraestructura localmente usando Terraform:

```bash
# Dirígete a la carpeta de infraestructura
cd infra

# Inicializa Terraform
terraform init

# Revisa los cambios a aplicar
terraform plan

# Aplica la configuración en AWS
terraform apply
```

---

## Arquitectura

![Arquitectura](aquitectura_pipeline.jfif)
