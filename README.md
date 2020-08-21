# Healthy_programmer

from pygame import mixer
from datetime import datetime
from time import time



def musiconloop(file, stopper):
    mixer.init()
    mixer.music.load("song.mp3")
    mixer.music.set_volume(0.7)
    mixer.music.play()

    while True:
        print("Press 'p' to pause, 'r' to resume")
        print("Press 'e' to exit the program")
        query = input("  ")

        if query == 'p':

            # Pausing the music
            mixer.music.pause()
        elif query == 'r':

            # Resuming the music
            mixer.music.unpause()
        elif query == 'e':

            # Stop the mixer
            mixer.music.stop()
            break

def log_now(msg):

    with open("mylogs.txt", "a") as f:
        f.write(f"{msg} {datetime.now()}\n")

if __name__ == "__main__":
    # musiconloop("water.mp3", "stop")
    init_water = time()
    init_eyes = time()
    inint_exercise = time()
    water_sec = 40*60
    exercises = 30*60
    eyes_ex = 45*60


    while True:
        if time() - init_water > water_sec:
            print("Water Drinking time. Enter 'drank' to stop the alarm.")
            musiconloop('water.mp3', 'drank')
            init_water = time()
            log_now("Drank Water at")

        if time() - init_eyes > eyes_ex:
            print("Eyes exercise time. Enter 'doneeyes' to stop the alarm.")
            musiconloop('eyes.mp3', 'doneeyes')
            init_eyes = time()
            log_now("Eyes Relaxed at")

        if time() - inint_exercise > exercises:
            print("Physical activity time. Enter 'donephy' to stop the alarm.")
            musiconloop('physical.mp3', 'doneghy')
            init_exercise = time()
            log_now("Physical activity at")

