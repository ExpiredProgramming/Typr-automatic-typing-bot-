# Typr-automatic-typing-bot-
Typr is a free automatic typing bot that lets you type a sentence into a text box and change the speed and delay before it starts. It's a great tool for people who want to improve their typing speed or practice their typing skills.

Typr is easy to use. Just type the sentence you want to type into the text box, and then set the speed and delay. You can also choose to have Typr start typing immediately or after a delay.

Once you've set your preferences, click the "Start Typing" button. Typr will start typing the sentence for you. You can watch Typr type, or you can close your eyes and try to type along.

Typr is a great way to improve your typing speed. It's also a great way to practice your typing skills. If you're looking for a way to improve your typing, Typr is a great option.

Here are some of the benefits of using Typr:

It's free to use.
It's easy to use.
It's customizable.
It's a great way to improve your typing speed.
It's a great way to practice your typing skills.
If you're looking for a free, easy-to-use, and customizable typing bot, Typr is a great option. It's a great way to improve your typing speed and practice your typing skills.

Here are some additional tips for using Typr:

Set the speed and delay to a comfortable level. You don't want Typr to type too fast or too slow.
Practice regularly. The more you use Typr, the better you'll become at typing.
Don't get discouraged if you don't see results immediately. It takes time and practice to improve your typing speed.
Have fun! Typr is a great way to improve your typing skills while having fun.

Here is the code! (dont forget to go into your CMD and type 1. pip install pyautpgui 2. pip install tkinter 3. (idk if you need this or not) pip install threading




import tkinter as tk
from tkinter import ttk
import threading
import time
import pyautogui
import random


class Typr:
    def __init__(self):
        self.text = ""
        self.speed = 0.1
        self.delay = 0.5
        self.accuracy = 0.9
        self.is_running = False
        self.thread = None

        self.window = tk.Tk()
        self.window.title("Typr")
        self.window.configure(bg="black")
        self.create_widgets()

    def create_widgets(self):
        title_label = tk.Label(self.window, text="Typr", fg="cyan", bg="black", font=("Arial", 24))
        title_label.pack(pady=10)

        text_frame = tk.Frame(self.window, bg="black")
        text_frame.pack()

        text_label = tk.Label(text_frame, text="Text:", fg="white", bg="black")
        text_label.pack(side=tk.LEFT)

        self.text_box = tk.Entry(text_frame, width=50)
        self.text_box.pack(side=tk.LEFT)

        speed_frame = tk.Frame(self.window, bg="black")
        speed_frame.pack()

        speed_label = tk.Label(speed_frame, text="Speed (words per minute):", fg="white", bg="black")
        speed_label.pack(side=tk.LEFT)

        self.speed_slider = ttk.Scale(speed_frame, from_=10, to=300, orient=tk.HORIZONTAL, length=200, command=self.update_speed)
        self.speed_slider.pack(side=tk.LEFT)

        delay_frame = tk.Frame(self.window, bg="black")
        delay_frame.pack()

        delay_label = tk.Label(delay_frame, text="Delay (sec):", fg="white", bg="black")
        delay_label.pack(side=tk.LEFT)

        self.delay_slider = ttk.Scale(delay_frame, from_=0, to=5, orient=tk.HORIZONTAL, length=200, command=self.update_delay)
        self.delay_slider.pack(side=tk.LEFT)

        accuracy_frame = tk.Frame(self.window, bg="black")
        accuracy_frame.pack()

        accuracy_label = tk.Label(accuracy_frame, text="Accuracy:", fg="white", bg="black")
        accuracy_label.pack(side=tk.LEFT)

        self.accuracy_slider = ttk.Scale(accuracy_frame, from_=0, to=1, orient=tk.HORIZONTAL, length=200, resolution=0.01, command=self.update_accuracy)
        self.accuracy_slider.pack(side=tk.LEFT)

        start_button = tk.Button(self.window, text="Start", fg="black", bg="cyan", command=self.start)
        start_button.pack(pady=10)

        self.window.mainloop()

    def update_speed(self, speed):
        self.speed = 60 / float(speed)

    def update_delay(self, delay):
        self.delay = float(delay)

    def update_accuracy(self, accuracy):
        self.accuracy = float(accuracy)

    def start(self):
        if self.is_running:
            return

        self.text = self.text_box.get()

        if not self.text:
            return

        self.is_running = True
        self.thread = threading.Thread(target=self.type_text)
        self.thread.start()

    def type_text(self):
        pyautogui.click()
        pyautogui.typewrite(self.text, interval=self.speed)
        self.is_running = False

typr = Typr()

