# Permisos en carpetas
Evita modificaciones incluso para root (opcional): Puedes usar el atributo immutable para proteger completamente la carpeta, incluso contra eliminación accidental:

- sudo chattr +i /ruta/de/la/carpeta

Para desactivar la protección: Cuando quieras permitir la eliminación o modificación, quita el atributo inmutable:

- sudo chattr +i /ruta/de/la/carpeta
