# API
## Python API

### What is an API?
Application Programming Interface. They are used to talk to any foreign server so we can gather
information from them
### Benefits of an API
- API saves a lot of time.
- Ease of integration
- Automating tasks

![img.png](img.png)

### Python requests
```python
import requests

r = requests.get("https://www.bbc.co.uk/")

print(r.status_code)
```
### America Weather Alerts by State
```python
import requests
import json


class WeatherAmerica:
    def __init__(self, state):
        self.state = state.upper()

    def different_states(self):
        """Lists the abbreviations for the different states"""
        pass

    def get_data(self):
        """Retrieves weather information from """
        headers = {"User-Agent":
        "learningapirequests, sam.dennis0000@gmail.com"}

        r = requests.get(f"https://api.weather.gov/alerts/active?area={self.state}", headers=headers)
        data = json.loads(r.content)
        with open(f"weather_{self.state}.json","w") as f:
            json.dump(data, f)


    def read_data(self):
        with open(f"weather_{self.state}.json","r") as f:
            data = json.loads(f.read())
        return data


current = WeatherAmerica("CA")
current.get_data()
```