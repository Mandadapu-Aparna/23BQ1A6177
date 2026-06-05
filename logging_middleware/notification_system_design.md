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


from datetime import datetime

def calculate_priority(notification):
    weight = WEIGHTS[notification.type]

    age_minutes = (datetime.now() - notification.timestamp).total_seconds() / 60

    score = (weight * 1000) - age_minutes

    return score

unread = [n for n in notifications if not n.read]

top_notifications = sorted(
    unread,
    key=calculate_priority,
    reverse=True
)

print("\nTop Notifications:")
for n in top_notifications:
    print(n.title, "->", calculate_priority(n))


from datetime import timedelta

notifications = [
    Notification(1, "Amazon Placement Drive", "PLACEMENT",
                 datetime.now() - timedelta(minutes=30)),

    Notification(2, "TCS Placement Drive", "PLACEMENT",
                 datetime.now() - timedelta(minutes=10)),

    Notification(3, "Semester Results", "RESULT",
                 datetime.now() - timedelta(minutes=20)),

    Notification(4, "Workshop Registration", "EVENT",
                 datetime.now() - timedelta(minutes=5)),

    Notification(5, "Hackathon Announcement", "EVENT",
                 datetime.now() - timedelta(minutes=15))
]

top10 = sorted(
    unread,
    key=calculate_priority,
    reverse=True
)[:10]
    

for n in notifications:
    print(n.title, "->", calculate_priority(n))
