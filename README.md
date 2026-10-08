[app.py](https://github.com/user-attachments/files/33181865/app.py)
[requirements.txt](https://github.com/user-attachments/files/33181913/requirements.txt)

[config.py](https://github.com/user-attachments/files/33181872/config.py)[requirements.txt](https://github.com/user-attachments/files/33181875/requirements.txt)[LEEME.md](https://github.com/user-attachments/files/33181877/LEEME.md)WHATSAPP_TOKEN=pega_aqui_el_token_permanente
PHONE_NUMBER_ID=# Chatbot de WhatsApp – Clínica de adelgazamiento

## Qué contiene
- `config.py`  → **único archivo que debes editar**: nombre, dirección, horario, tratamientos y precios.
- `app.py`, `requirements.txt`, `Procfile` → no los toques.
- `.env.example` → lista de las 4 claves que vas a necesitar.

## Paso 1. Personaliza `config.py`
Ábrelo con el Bloc de notas y cambia solo el texto entre comillas (nombre de la clínica, dirección, horario, precios, descripciones).

## Paso 2. Sube los archivos a GitHub
1. Crea una cuenta en github.com y un repositorio **privado** nuevo.
2. Pulsa *Add file → Upload files* y arrastra `app.py`, `config.py`, `requirements.txt` y `Procfile`. Pulsa *Commit changes*.

## Paso 3. Ponlo en línea con Render
1. Entra a render.com, crea cuenta y elige *New → Web Service*. Conecta tu GitHub y escoge el repositorio.
2. Configura:
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `gunicorn app:app`
3. En *Environment* agrega estas 4 variables:
   - `WHATSAPP_TOKEN` = tu token permanente
   - `PHONE_NUMBER_ID` = tu Phone Number ID
   - `VERIFY_TOKEN` = una palabra secreta que inventes (ej: `silueta2026clave`)
   - `ADVISOR_NUMBER` = número de la asesora con código de país, sin `+` (ej: `51999999999`)
4. Pulsa *Create Web Service*. Al terminar te da una dirección tipo `https://tu-bot.onrender.com`.
   Si la abres en el navegador debe decir "Chatbot activo".

> El plan gratuito de Render "se duerme" tras un rato sin uso y puede tardar en responder o perder mensajes.
> Para una clínica con clientes reales usa un plan de pago básico.

## Paso 4. Conecta el webhook en Meta
1. En developers.facebook.com abre tu app → *WhatsApp → Configuración (Configuration)*.
2. En *Webhook* pulsa *Editar* y completa:
   - URL de devolución de llamada: `https://tu-bot.onrender.com/webhook`
   - Token de verificación: el mismo `VERIFY_TOKEN` del paso 3
3. Pulsa *Verificar y guardar*.
4. En *Campos del webhook* suscríbete a **messages**.

## Paso 5. Prueba
Escribe "hola" al número de WhatsApp de la app. Debe aparecer el menú.
Con el número de prueba de Meta solo puedes escribir desde teléfonos que registraste como destinatarios.
Para que respondan clientes reales: agrega tu número real y pasa la app a modo **Live/Publicada** (Meta pide una URL de política de privacidad).

## Cosas que debes saber
- **Aviso a la asesora:** WhatsApp solo deja al bot escribirle libremente si ella le escribió en las últimas 24 horas. Haz que la asesora le mande "hola" al bot cada día, o pide que se agregue un aviso por plantilla/correo.
- **Memoria:** si el servidor se reinicia, los chats en curso se reinician (el cliente solo vuelve a ver el menú).
- **Publicidad:** evita prometer resultados ("baja X kilos") en el bot o en anuncios; Meta es estricta con salud y pérdida de peso.
pega_aqui_el_phone_number_id
VERIFY_TOKEN=inventa_una_palabra_secreta
ADVISOR_NUMBER=51999999999
[LEEME.md](https://github.com/user-attachments/files/33181922/LEEME.md)
