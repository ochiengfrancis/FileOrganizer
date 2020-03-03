# FileOrganizer
#This is a python script that automatically saves documents/files to a folder of your choice without having to do it Manually.

from watchdog import observers
from watchdog.events import PatternMatchingEventHandler, FileSystemEventHandler
import json
import time
import os


class FileHandler(FileSystemEventHandler):
    i = 1

    def on_modified(self, event):
        for filename in os.listdir(home):
            source = home + "/" + filename
            new_folder = destination + "/" + filename
            os.rename(source, new_folder)


home = "/home/franc/Downloads"
destination = "/home/franc/Music/newfolder"

event_handler = FileHandler()
observer = observers.Observer()
observer.schedule(event_handler, home, recursive=True)
observer.start()

try:
    while True:
        time.sleep(10)
except KeyboardInterrupt:
    observer.stop()
observer.join()
