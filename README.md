# Simulador Oficial de Exámenes FIR (2020-2025)

[![GitHub Pages Deployment](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-blue?style=for-the-badge&logo=github)](https://jjdmochon.github.io/FIR/)
[![Licencia](https://img.shields.io/badge/Licencia-Educativa-green?style=for-the-badge)](LICENSE)
[![Ministerio de Sanidad](https://img.shields.io/badge/Datos-Ministerio%20de%20Sanidad-red?style=for-the-badge)](https://fse.mscbs.gob.es/)

Plataforma interactiva de preparación y simulación de exámenes oficiales para aspirantes a la prueba selectiva de **Farmacéutico Interno Residente (FIR)**, convocada anualmente por el Ministerio de Sanidad del Gobierno de España.

Incluye los **6 exámenes oficiales completos (2020 a 2025)** con todas sus preguntas, opciones, estructuras químicas en alta definición, plantillas oficiales definitivas de respuestas y soporte para preguntas anuladas.

---

## 🚀 Acceso Rápido y Demostración en Línea

La aplicación está diseñada para desplegarse directamente en **GitHub Pages**:
🔗 **[https://jjdmochon.github.io/FIR/](https://jjdmochon.github.io/FIR/)**

---

## 🏛️ Arquitectura Técnica

Para garantizar la máxima velocidad de carga, disponibilidad continua y cero costes de servidor o infraestructura, se ha implementado una arquitectura web **Single-Page Application (SPA) 100% Estática**:

- **Cero dependencias de servidor / Cero bundlers pesados**: No requiere procesos de compilación complejos (`npm run build` o Webpack) que puedan fallar en entornos de integración continua.
- **Rendimiento Instantáneo (< 30 ms)**: Todos los exámenes (1.235 preguntas oficiales) están pre-estructurados en `data/exams.js`, permitiendo un cambio instantáneo de examen y navegación a 60 FPS sin latencias de red.
- **Modo Offline & Resiliencia**: Almacenamiento local mediante `localStorage` para guardar el progreso del aspirante en tiempo real (respuestas seleccionadas, dudas marcadas, tiempo restante y estado del examen). Si se cierra la pestaña o se recarga la página, el examen continúa exactamente donde se dejó.
- **Diseño Responsive & Accesible**: Maquetado con **Tailwind CSS**, soporte para **Modo Claro / Modo Oscuro**, tipografía optimizada para lectura prolongada y atajos de teclado para responder con rapidez.

---

## 📋 Convocatorias Oficiales Incluidas

| Convocatoria | Preguntas | Estructuras / Figuras | Cuaderno Oficial | Plantilla Oficial |
| :--- | :---: | :---: | :--- | :--- |
| **FIR 2025** | 210 | 15 imágenes HD | `FIR2025/Cuaderno_2025_F_0_C.pdf` | `FIR2025/respuestascorrectas 2025.pdf` |
| **FIR 2024** | 210 | 19 imágenes HD | `FIR2024/Cuaderno_2024_FARMACIA_0_C.pdf` | `FIR2024/respuestasCorrectas 024.pdf` |
| **FIR 2023** | 210 | 11 imágenes HD | `FIR2023/Cuaderno_2023_FARMACIA_0_C.pdf` | `FIR2023/Respuestas correctas 2023 examen 0.pdf` |
| **FIR 2022** | 210 | 2 imágenes HD | `FIR2022/Cuaderno_2022_FARMACIA_0_C.pdf` | `FIR2022/respuestas_2022.pdf` |
| **FIR 2021** | 210 | Texto completo | `FIR2021/Cuaderno_2021_FARMACIA_0_C.pdf` | `FIR2021/respuestas_2021.pdf` |
| **FIR 2020** | 185 | Texto completo | `FIR2020/Cuaderno_2020_FARMACIA_0_C.pdf` | `FIR2020/respuestas_2020.pdf` |

*Nota: En la convocatoria 2020 (formato COVID), el examen constó oficialmente de 175 preguntas ordinarias + 10 de reserva (total 185 preguntas).*

---

## 🎯 Funcionalidades Principales para el Aspirante FIR

1. **Modo Simulacro Real**:
   - Temporizador oficial de **4 horas y 30 minutos** con avisos visuales en el último cuarto de hora.
   - **Baremo oficial del Ministerio de Sanidad**:
     $$\text{Puntuación Neta} = (3 \times \text{Aciertos}) - \text{Fallos}$$
   - Las preguntas no contestadas computan 0 puntos.
   - Las preguntas anuladas por la Comisión Calificadora son identificadas automáticamente y no penalizan (0 puntos).
   - Corrección global al finalizar la prueba con desglose completo y porcentaje de efectividad.
2. **Modo Estudio / Flashcards**:
   - Corrección instantánea con código de colores (verde para aciertos, rojo para fallos).
   - Botón **Ver Respuesta** para comprobación directa.
3. **Hoja de Respuestas Interactiva (Rejilla de 210 casillas)**:
   - Panel lateral con las 210 casillas numeradas idénticas a la plantilla del Ministerio.
   - Código de colores en tiempo real: contestadas (azul), dudosas/para revisar (amarillo), sin responder (gris).
   - Salto inmediato a cualquier pregunta con un solo clic.
4. **Visor de Estructuras Químicas en Alta Resolución**:
   - Recortes nítidos de fórmulas esqueléticas, esquemas de síntesis, diagramas y espectros a 288 DPI.
   - Clic para ampliar en ventana modal a pantalla completa.
5. **Atajos de Teclado**:
   - `1`, `2`, `3`, `4`: Seleccionar opción.
   - `→` o `J`: Pregunta siguiente.
   - `←` o `K`: Pregunta anterior.
   - `M`: Marcar / desmarcar como dudosa (⚑).
   - `Espacio`: Ver respuesta oficial (en Modo Estudio).
   - `Esc`: Cerrar visor de imagen o resultados.

---

## 📁 Estructura del Repositorio

```text
FIR/
├── index.html               # Aplicación web principal (SPA responsive para GitHub Pages)
├── README.md                # Documentación del proyecto
├── .gitignore               # Exclusiones de sistema y ficheros temporales
├── data/                    # Base de datos unificada en formato JSON y JS
│   ├── exams.js             # Objeto global para carga inmediata en cliente
│   ├── fir_2020.json
│   ├── fir_2021.json
│   ├── fir_2022.json
│   ├── fir_2023.json
│   ├── fir_2024.json
│   └── fir_2025.json
├── FIR2020/                 # Cuaderno original, plantilla oficial y visor individual
├── FIR2021/
├── FIR2022/
│   └── images/              # Estructuras químicas y figuras
├── FIR2023/
│   └── images/
├── FIR2024/
│   └── images/
└── FIR2025/
    ├── images/              # 15 imágenes oficiales extraídas y optimizadas
    ├── FIR-2025-0.html      # Visor autónomo de la convocatoria 2025
    ├── Cuaderno_2025_F_0_C.pdf
    └── respuestascorrectas 2025.pdf
```

---

## 🛠️ Despliegue en GitHub Pages

Para alojar la web de forma gratuita y permanente en GitHub Pages:

1. El repositorio está configurado y sincronizado en:
   `https://github.com/jjdmochon/FIR`
2. En GitHub, acceder a **Settings** > **Pages** (`https://github.com/jjdmochon/FIR/settings/pages`).
3. En **Build and deployment** > **Source**, seleccionar `Deploy from a branch`.
4. En **Branch**, seleccionar `main` y la carpeta `/ (root)`.
5. Pulsar **Save**. En un minuto, la web estará disponible en:
   **`https://jjdmochon.github.io/FIR/`**

---

## 📄 Créditos y Licencia

Los enunciados de los exámenes, imágenes de examen y plantillas oficiales pertenecen al **Ministerio de Sanidad del Gobierno de España**. Este repositorio y su interfaz interactiva han sido desarrollados con fines exclusivamente docentes, divulgativos y de preparación académica para futuros profesionales farmacéuticos especialistas.
