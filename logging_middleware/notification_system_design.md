from datetime import datetime

class Notification:
    def __init__(self, id, title, type, timestamp, read=False):
        self.id = id
        self.title = title
        self.type = type
        self.timestamp = timestamp
        self.read = read


WEIGHTS = {
    "PLACEMENT": 3,
    "RESULT": 2,
    "EVENT": 1
}

notifications = [
    Notification(
        1,
        "Amazon Placement Drive",
        "PLACEMENT",
        datetime.now()
    ),

    Notification(
        2,
        "Semester Results Published",
        "RESULT",
        datetime.now()
    ),

    Notification(
        3,
        "Cultural Fest Registration",
        "EVENT",
        datetime.now()
    )
]

for n in notifications:
    print(n.title, n.type)
