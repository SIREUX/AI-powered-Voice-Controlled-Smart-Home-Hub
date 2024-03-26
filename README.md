# AI-powered-Voice-Controlled-Smart-Home-Hub
Créez un hub domotique intelligent contrôlé par la voix et alimenté par l'IA, permettant aux utilisateurs de gérer facilement leurs appareils connectés.
import speech_recognition as sr

# Mock functions to simulate device control
def control_lights(command):
    if "on" in command:
        print("Turning the lights ON")
    elif "off" in command:
        print("Turning the lights OFF")
    else:
        print("Command not recognized. Please say 'lights on' or 'lights off'.")

def control_thermostat(command):
    if "up" in command:
        print("Turning the temperature UP")
    elif "down" in command:
        print("Turning the temperature DOWN")
    else:
        print("Command not recognized. Please say 'temperature up' or 'temperature down'.")

def listen_and_respond():
    # Initialize recognizer
    r = sr.Recognizer()

    # Use the default microphone as the audio source
    with sr.Microphone() as source:
        print("Listening for commands...")
        audio = r.listen(source)

    try:
        # Recognize speech using Google Web Speech API
        command = r.recognize_google(audio).lower()
        print(f"Recognized command: {command}")

        # Simple command routing
        if "light" in command:
            control_lights(command)
        elif "temperature" in command:
            control_thermostat(command)
        else:
            print("Sorry, I didn't understand that.")
    except sr.UnknownValueError:
        print("Google Speech Recognition could not understand the audio")
    except sr.RequestError as e:
        print(f"Could not request results from Google Speech Recognition service; {e}")

# Main loop
if __name__ == "__main__":
    while True:
        listen_and_respond()
