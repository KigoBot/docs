---
hide:
  - navigation
---

# Problemas frecuentes

Las preguntas que más recibe el autor, con respuestas cortas. Si tu problema no está aquí, mira las páginas específicas de cada tema o pregunta en el [servidor de soporte](https://discord.gg/wmky5nBRR2).

## Las 10 más frecuentes

### 1. El bot no me deja usar un comando

Probablemente tu rol no tiene el permiso necesario. Por ejemplo, para usar `/ban` necesitas el permiso "Banear miembros". Revisa `Configuración del servidor > Roles > tu rol > Permisos`.

Más detalles: [No puedo usar este comando](no-puedo-usar-comando.md).

### 2. No me llega el código de verificación

El usuario probablemente tiene los DMs cerrados. Hay que cambiarlos en `Ajustes de usuario > Privacidad y seguridad > Permitir mensajes directos de miembros del servidor`.

Más detalles: [No me llega el código de verificación](codigo-verificacion.md).

### 3. ¿Por qué pide tantos permisos al añadirlo?

Porque hace muchas cosas. Los permisos son los mismos que tendría un equipo de mods humanos. Sin permisos, no podría moderar. Más detalles: [Permisos que pide](../empezar/permisos.md).

### 4. ¿Pierdo la configuración si quito el bot?

No. La configuración se guarda en la base de datos de Kigo asociada a tu servidor. Si vuelves a añadir el bot, la recuperas.

Si quieres un backup por si acaso, usa `/configuración` → **Backups** → **Exportar**.

### 5. ¿Funciona en mensajes directos (DMs)?

No. Kigo solo funciona en servidores. Los DMs están fuera de su scope.

### 6. ¿Cómo cambio de owner del servidor sin perder la configuración?

La configuración está vinculada al **ID del servidor**, no al owner. Cambiar de owner no afecta a Kigo. Solo asegúrate de que el nuevo owner también pueda usar los comandos (los que requieren OWNER_GUILD).

### 7. ¿Hay web o app móvil?

No. Toda la gestión se hace desde Discord. Si quieres automatizar cosas, puedes usar webhooks o bots externos que se integren con Kigo.

### 8. ¿Puedo usar Kigo en canales de voz?

No. Kigo no entra a canales de voz ni reproduce audio. Es exclusivamente un bot de moderación y protección.

### 9. ¿Cuánto cuesta?

Kigo es gratis. Premium es opcional, no se compra con dinero: se obtiene por códigos que se distribuyen en eventos y colaboraciones. Más detalles: [Qué es premium](../premium/que-es.md).

### 10. ¿Cómo reporto un bug o pido una feature?

En el [servidor de soporte](https://discord.gg/wmky5nBRR2) hay un canal `#bugs` y un canal `#sugerencias`. Describe el problema con detalle (qué pasó, qué esperabas, capturas si es posible).

## Si no encuentras tu problema

Las siguientes páginas tienen soluciones a problemas más específicos:

- [No me llega el código](codigo-verificacion.md)
- [El bot no responde](bot-no-responde.md)
- [No puedo usar este comando](no-puedo-usar-comando.md)
- [Recuperar configuración](recuperar-backup.md)
- [Cambiar de owner del servidor](migrar-servidor.md)

Si después de leer todo sigues atascado, pregunta en el [servidor de soporte](https://discord.gg/wmky5nBRR2) con la mayor cantidad de detalles posible (capturas, mensajes de error, qué has intentado).
