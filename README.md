# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date: 16/10/25
# Register no: 212222240101
## Aim:
To learn how to design effective prompts for AI tools to generate Python code, compare API outputs, and give insights.

## **2. AI Tools Required**

1. **ChatGPT / Gemini / Claude**
   – For generating Python code, explanations, and insights.
2. **Any REST API Platform**
   – OpenWeatherMap API
   – WeatherAPI.com
3. **VS Code / Jupyter Notebook (Optional)**
   – To test the generated Python code.
4. **JSON Viewer (Optional)**
   – For viewing formatted API responses.

## **3. Steps**

1. Identify two APIs to compare (OpenWeatherMap & WeatherAPI are used in this experiment).
2. Design prompts asking the AI to generate Python code to fetch data from both APIs.
3. Run the AI-generated code and collect output JSON from both APIs.
4. Create a prompt asking the AI to compare the outputs.
5. Ask the AI to produce insights and next steps.
6. Document all prompts, code, comparison tables, and final reflections.
7. Prepare the final experiment report.

## **4. Designed Prompts and AI Responses**

## **Stage 1: Prompt for Generating Python Code**

## **Prompt 1**

Generate Python code that connects to two public APIs: 
(1) OpenWeatherMap API to get current weather, and 
(2) WeatherAPI.com for the same city. The code should:

– Accept city name as input

– Return temperature, humidity, and condition

– Use error handling

– Format output in clean JSON

– Add comments explaining each step.

### **AI Response (Code + Explanation)**

### **Generated Python Code**

```python
import requests

def fetch_openweather(city):
    api_key = "YOUR_OPENWEATHER_KEY"
    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
    try:
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()

        return {
            "source": "OpenWeatherMap",
            "temperature": data["main"]["temp"],
            "humidity": data["main"]["humidity"],
            "condition": data["weather"][0]["description"]
        }
    except Exception as e:
        return {"error": str(e)}

def fetch_weatherapi(city):
    api_key = "YOUR_WEATHERAPI_KEY"
    url = f"http://api.weatherapi.com/v1/current.json?key={api_key}&q={city}"
    try:
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()

        return {
            "source": "WeatherAPI",
            "temperature": data["current"]["temp_c"],
            "humidity": data["current"]["humidity"],
            "condition": data["current"]["condition"]["text"]
        }
    except Exception as e:
        return {"error": str(e)}

city = "Chennai"
ow_data = fetch_openweather(city)
wa_data = fetch_weatherapi(city)

print("OpenWeatherMap:", ow_data)
print("WeatherAPI:", wa_data)
```

### **Explanation**

* Two functions are created to fetch weather data.
* JSON output is formatted for easy comparison.
* Errors are handled with `try–except`.
* The program prints the weather details for a given city from both APIs.

## **Stage 2: Prompt for Comparing API Outputs**

## **Prompt 2**

**“Compare the JSON outputs from OpenWeatherMap and WeatherAPI. Highlight differences in temperature, humidity, and condition. Show a table and give a short explanation.”**

## **AI Response (Comparison Output)**

## **API Outputs Compared**

**OpenWeatherMap Output (Example):**

```
{
  "source": "OpenWeatherMap",
  "temperature": 31.0,
  "humidity": 70,
  "condition": "scattered clouds"
}
```

**WeatherAPI Output (Example):**

```
{
  "source": "WeatherAPI",
  "temperature": 30.4,
  "humidity": 74,
  "condition": "Partly cloudy"
}
```

## **Comparison Table**

| **Parameter**    | **OpenWeatherMap** | **WeatherAPI** |
| ---------------- | ------------------ | -------------- |
| Temperature (°C) | 31.0               | 30.4           |
| Humidity (%)     | 70                 | 74             |
| Condition        | scattered clouds   | Partly cloudy  |


### **Comparison Summary**

Both APIs show very similar weather data. The temperature differs by only 0.6°C, humidity varies by 4%, and condition wording differs slightly. These small variations occur due to different sensors and update intervals. Both APIs are reliable for real-time weather monitoring.

## **Stage 3: Prompt for Insights**

### **Prompt 3**

**“Based on the comparison, give insights and suggest next steps for improving the project. Output in bullet points.”**

## **AI Response (Insights + Next Steps)**

### **Insights**

* Both APIs provide consistent temperature and humidity values.
* Variations are small and acceptable for real-time weather applications.
* WeatherAPI gives more descriptive conditions, while OpenWeatherMap provides richer metadata.

### **Next Steps**

* Log data periodically to study trends over time.
* Visualize temperature and humidity differences using graphs.
* Add additional weather parameters like UV index, wind speed, or AQI.
* Deploy the code as a mini web dashboard.

## **5. Reflection Note**

This experiment improved my understanding of how to design effective prompts for coding tasks. Clear prompts with detailed instructions resulted in accurate and complete code generation. When I included specific requirements such as JSON formatting and detailed comparison steps, the AI responses became more structured and useful.

The comparison stage helped me understand how to ask the AI for formatted outputs like tables and summaries. Insights became more meaningful when I added context such as “suggest next steps.” Overall, I learned that the more precise and detailed the prompt, the better the AI output. This skill will be valuable for future project development.

## Result:
The experiment was successfully carried out, and the AI generated correct code, comparisons, and insights based on the prompts. Students understood that clear prompts lead to accurate and useful AI responses.



