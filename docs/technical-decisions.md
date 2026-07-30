# Decisiones técnicas destacadas

Este documento resume decisiones de diseño relevantes sin publicar código propietario ni lógica interna replicable.

## 1. Producto multi-tenant

LeadBOT fue diseñado para que diferentes clientes usen la misma plataforma con datos, configuración, módulos y conocimiento separados.

## 2. Arquitectura modular

El producto distingue capacidades core y módulos opcionales. Esto permite activar funcionalidades por tipo de cliente sin duplicar la aplicación.

Capacidades core:

- inbox;
- bot;
- conocimiento;
- leads;
- derivaciones;
- seguimiento comercial.

Módulos opcionales:

- servicios y turnos;
- comercio;
- integraciones adicionales;
- automatizaciones avanzadas.

## 3. IA con contexto controlado

El motor conversacional no depende sólo de una respuesta libre del modelo. Antes de responder, el sistema prepara contexto útil: historial, módulos activos, información del negocio y estado comercial acumulado.

Después de responder, se aplican validaciones para reducir errores como:

- repetición de preguntas ya respondidas;
- pérdida de contexto;
- filtrado de razonamiento interno;
- uso de módulos no activos;
- preguntas múltiples cuando conviene avanzar de a un dato.

## 4. Handoff humano como estado real

La derivación no es sólo un texto en el chat. El sistema registra una solicitud de atención y cambia el estado de la conversación para que el bot no siga contestando automáticamente cuando ya debe intervenir una persona.

## 5. Reglas determinísticas para operaciones críticas

La IA ayuda a comprender y redactar, pero no decide por sí sola operaciones sensibles. Las confirmaciones operativas deben pasar por reglas del sistema.

## 6. Procesamiento por colas

El ingreso de mensajes y el procesamiento conversacional están desacoplados. Esto mejora tolerancia a fallos y permite escalar workers según carga.

## 7. Documentación pública limitada

Por tratarse de un producto propietario, este repositorio muestra arquitectura, funcionalidades y decisiones generales, pero no incluye elementos que permitan copiar el producto completo.
