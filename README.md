# SpeechRecognition
import speech_recognition as sr

# initialize recognizer
r = sr.Recognizer()

# define microphone as source
with sr.Microphone() as source:
    print("Speak now...")
    # adjust for ambient noise
    r.adjust_for_ambient_noise(source)
    # listen for user input
    audio = r.listen(source)

try:
    # recognize speech using Google Speech Recognition
    text = r.recognize_google(audio)
    print("You said: " + text)

except sr.UnknownValueError:
    print("Sorry, I could not understand what you said.")

except sr.RequestError as e:
    print("Sorry, could not request results from Google Speech Recognition service; {0}".format(e))
