# EA Adaptativo Multi-Estrategia para MetaTrader 4 (MQL4)

Un Asesor Experto (EA) avanzado y de código abierto para MetaTrader 4, diseñado para operar de forma adaptativa. En lugar de seguir reglas fijas, este bot analiza el contexto del mercado en tiempo real y selecciona la estrategia de compra más adecuada para la situación actual.


---

## 🚀 Características Principales

* **🧠 Motor de Decisión Adaptativo:** El núcleo del bot. Analiza la fuerza de la tendencia (con Medias Móviles y ADX) y la volatilidad (con ATR) para decidir qué hacer.
* **🧩 Lógica Multi-Estrategia:** Incluye un arsenal de cuatro estrategias de compra distintas:
    * Retroceso a niveles de Fibonacci (Ondas de Elliott).
    * Ruptura de patrones de Triángulo (Ondas de Elliott).
    * Compra en retroceso (pullback) a la Media Móvil lenta.
    * *Framework listo para añadir una estrategia de ruptura de máximos.*
* **🛡️ Gestión de Riesgo Avanzada:** Equipado con mecanismos de protección de capital para un trading más seguro:
    * **Stop de Pérdida Diaria:** Detiene la operativa si se alcanza un límite de pérdida diario.
    * **Stop por Pérdidas Consecutivas:** Pausa el bot después de una racha de pérdidas para evitar mayores daños.
    * **Cálculo de Lote Dinámico:** Ajusta el tamaño de la posición automáticamente según el porcentaje de riesgo definido.
* **📈 Solo Compras (Long-Only):** Optimizado para operar únicamente a favor de tendencias alcistas, filtrando las señales de baja probabilidad en mercados bajistas.
* **📊 Panel de Control y Reportes:** Incluye un panel visual en el gráfico para un control rápido (Pausa/Reanudar) y genera informes de rendimiento periódicos (semanales o mensuales).
* **⚙️ Altamente Configurable:** Todos los parámetros de los indicadores, estrategias y mecanismos de seguridad son totalmente personalizables a través de los `Inputs`.

---

## 🛠️ Cómo Funciona: La Estrategia

El EA opera bajo una jerarquía de decisión clara:

1.  **Filtro Maestro de Tendencia:** La primera y más importante regla. El bot solo considerará operar si la tendencia general es alcista, determinada por el cruce de una media móvil rápida (ej. 50 EMA) por encima de una lenta (ej. 200 EMA). Si no se cumple, el bot permanece inactivo.
2.  **Análisis de Contexto:** Si la tendencia es alcista, el "Motor de Decisión" entra en juego. Mide la **fuerza** de esa tendencia con el indicador ADX para clasificar el mercado en uno de tres estados:
    * **Mercado en Rango:** ADX bajo. La mejor estrategia es buscar patrones de consolidación.
    * **Tendencia Fuerte:** ADX alto. La mejor estrategia es buscar compras en retrocesos (pullbacks).
    * **Tendencia Moderada:** ADX en un nivel intermedio. Se buscan oportunidades de alta calidad.
3.  **Ejecución Selectiva:** Basado en el contexto, el motor elige y ejecuta **solo una** de las estrategias disponibles, la que mejor se adapte a la situación actual del mercado.

---

## ⚙️ Instalación

1.  Descarga el archivo `ElliotWaveEA.mq4`.
2.  En tu plataforma MetaTrader 4, ve a **Archivo -> Abrir Carpeta de Datos**.
3.  Navega a la carpeta `MQL4/Experts/`.
4.  Copia y pega el archivo `.mq4` en esta carpeta.
5.  Vuelve a MetaTrader 4, ve al panel "Navegador", haz clic derecho en "Asesores Expertos" y selecciona **Actualizar**.
6.  El bot `ElliotWaveEA` aparecerá en la lista, listo para ser usado.

---

## 🕹️ Uso y Optimización

Este EA está diseñado para ser optimizado para diferentes activos y timeframes (M30, H1, H4). El flujo de trabajo recomendado es:

1.  Usa el **Probador de Estrategias** de MT4 en modo **"Optimización"** para encontrar los parámetros de entrada (`Inputs`) que generen los mejores resultados (bajo Drawdown y alto Factor de Beneficios) para un activo y timeframe específico.
2.  **Guarda** esa configuración óptima como un archivo `.set` (ej. `XAUUSD_H1_Seguro.set`).
3.  Cuando quieras usar el bot en un gráfico en vivo, simplemente **Carga** el archivo `.set` correspondiente para aplicar instantáneamente la configuración probada.

---

## 🤝 Cómo Contribuir

¡Este es un proyecto de código abierto y toda ayuda es bienvenida!

1.  **Reporta Bugs:** Si encuentras un error, por favor abre un "Issue" (Incidencia) detallando el problema.
2.  **Sugiere Mejoras:** ¿Tienes una idea para una nueva estrategia o una mejora en el motor de decisión? Abre un "Issue" para discutirla.
3.  **Envía Pull Requests:** Si quieres aportar código:
    * Haz un "Fork" del repositorio.
    * Crea una nueva rama para tu mejora (`git checkout -b mejora/nueva-estrategia`).
    * Haz tus cambios y haz "Commit".
    * Envía un "Pull Request" con una descripción clara de los cambios.

---

## 📜 Licencia

Este proyecto está bajo la **Licencia MIT**. Esto significa que eres libre de usar, modificar y distribuir el software, incluso para fines comerciales, siempre que incluyas el aviso de copyright original.

---

## ⚠️ Descargo de Responsabilidad (Disclaimer)

El trading de divisas y derivados conlleva un alto nivel de riesgo y puede no ser adecuado para todos los inversores. El rendimiento pasado no es un indicador de resultados futuros.

Este software se proporciona "TAL CUAL", sin ninguna garantía. Se distribuye con fines educativos y de investigación. El uso de este Asesor Experto en una cuenta de trading real es bajo tu propia responsabilidad. Los autores y colaboradores de este proyecto no se hacen responsables de ninguna pérdida financiera que puedas sufrir. **Opera siempre primero en una cuenta demo.**
