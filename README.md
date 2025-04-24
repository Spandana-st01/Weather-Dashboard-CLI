import requests

API_KEY = "your_api_key_here"  # Get yours from https://openweathermap.org/api
BASE_URL = "http://api.openweathermap.org/data/2.5/weather"

def get_weather(city):
    params = {
        "q": city,
        "appid": API_KEY,
        "units": "metric"
    }
    response = requests.get(BASE_URL, params=params)
    data = response.json()

    if response.status_code == 200:
        print(f"\nWeather in {city.capitalize()}:")
        print(f"Temperature: {data['main']['temp']}°C")
        print(f"Humidity: {data['main']['humidity']}%")
        print(f"Wind Speed: {data['wind']['speed']} m/s")
        print(f"Condition: {data['weather'][0]['description'].capitalize()}")
    else:
        print(f"\nError: {data['message'].capitalize()}")

if _name_ == "_main_":
    print("=== Weather Dashboard ===")
    city = input("Enter city name: ")
    get_weather(city)
