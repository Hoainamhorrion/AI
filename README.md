
import speech_recognition
import pyttsx3
from datetime import date

robot_ear = speech_recognition.Recognizer()
robot_mouth = pyttsx3.init()
robot_brain = ""

with speech_recognition.Microphone() as mic:
	print("Robot: I'm listening...")
	audio = robot_ear.listen(mic)
print("Robot: ...")
try:
	you = robot_ear.recognize_google(audio)
except:
	you = ""
print("You:" + you)

if you == "":
	robot_brain = " I can't hear you, try again"
elif you == "hello":
	robot_brain = " hello Hoai Nam"	
elif you == "today":
	today = date.today()
	robot_brain = today.strftime("%B %d, %Y")
elif you == "what is my name":
	robot_brain = "Nguyen Hoai Nam"
else:
	robot_brain = ("Can you repeat it")

print("Robot: " + robot_brain)

robot_mouth.say(robot_brain)
robot_mouth.runAndWait()
