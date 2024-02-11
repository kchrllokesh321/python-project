# python-project
getting weather infromation
import requests

def get_weather(city):
    api_key = "YOUR_API_KEY"  # Replace with your actual OpenWeatherMap API key
    base_url = "http://api.openweathermap.org/data/2.5/weather?"

    complete_url = base_url + "appid=" + api_key + "&q=" + city 
    response = requests.get(complete_url)

    if response.status_code == 200:
        data = response.json()
        report = f"""
        Weather in {city}:
        Temperature: {round(data['main']['temp'] - 273.15, 2)} °C
        Feels like: {round(data['main']['feels_like'] - 273.15, 2)} °C
        Weather Description: {data['weather'][0]['description']}
        """
        print(report)
    else:
        print("Error: City not found or API issue.")

if __name__ == "__main__":
    city = input("Enter city name: ")
    get_weather(city)
