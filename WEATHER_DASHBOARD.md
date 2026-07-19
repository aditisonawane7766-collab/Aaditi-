# Weather Dashboard 🌤️

A comprehensive **Real-time Weather Dashboard** application built with **Spring Boot 3.2** backend and **React** frontend, integrating with OpenWeatherMap API.

## 🌟 Features

✅ **Real-time Weather Data** - Current weather for any city worldwide
✅ **Weather Forecast** - 5-day forecast with detailed predictions
✅ **Location Search** - Search weather by city name
✅ **GPS Integration** - Get weather for current location
✅ **Weather Alerts** - Temperature, humidity, wind speed alerts
✅ **Beautiful UI** - Modern, responsive weather dashboard
✅ **Multiple Units** - Celsius and Fahrenheit support
✅ **Weather Icons** - Visual weather condition indicators
✅ **Sunrise/Sunset** - Solar timing information
✅ **Wind Speed & Direction** - Detailed wind information

## 🛠 Technology Stack

### Backend
- **Spring Boot 3.2.0** - Framework
- **Spring Web** - REST API
- **RestTemplate** - HTTP client for API calls
- **Lombok** - Code generation
- **Jackson** - JSON processing
- **Java 21** - Programming language
- **Maven** - Build tool

### Frontend (React)
- **React 18+** - UI framework
- **Axios** - HTTP client
- **React Router** - Navigation
- **CSS3** - Responsive styling
- **Chart.js** - Temperature charts

### External API
- **OpenWeatherMap API** - Weather data provider

## 📋 Prerequisites

- Java 21 or higher
- Maven 3.8.0+
- Node.js 18+
- npm or yarn
- OpenWeatherMap API key (free tier available)

## 🚀 Quick Start

### Step 1: Get OpenWeatherMap API Key

1. Visit: https://openweathermap.org/api
2. Sign up for free account
3. Generate API key from your account dashboard
4. Copy the API key

### Step 2: Backend Setup

```bash
# Clone repository
git clone https://github.com/aditisonawane7766-collab/Aaditi-.git
cd Aaditi-

# Set API Key (Option 1: Environment Variable)
export WEATHER_API_KEY=your_api_key_here

# Or Option 2: Update application-weather.yml
# Edit: src/main/resources/application-weather.yml
# Replace: your_openweathermap_api_key_here with actual key

# Build project
mvn clean install

# Run application
mvn spring-boot:run -Dspring.config.name=application,application-weather
```

Backend runs at: **http://localhost:8081/api**

### Step 3: Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start development server
npm start
```

Frontend runs at: **http://localhost:3000**

## 📡 API Endpoints

### Weather Endpoints

| Method | Endpoint | Description | Example |
|--------|----------|-------------|---------|
| GET | `/weather/city/{city}` | Get weather by city name | `/weather/city/London` |
| GET | `/weather/coordinates?latitude=40.7128&longitude=-74.0060` | Get weather by GPS coordinates | `/weather/coordinates?latitude=40.7128&longitude=-74.0060` |
| GET | `/weather/health` | API health check | `/weather/health` |

### Forecast Endpoints

| Method | Endpoint | Description | Example |
|--------|----------|-------------|---------|
| GET | `/forecast/city/{city}` | Get 5-day forecast by city | `/forecast/city/Tokyo` |
| GET | `/forecast/coordinates?latitude=35.6762&longitude=139.6503` | Get forecast by coordinates | `/forecast/coordinates?latitude=35.6762&longitude=139.6503` |

## 🔍 API Response Example

### Current Weather Response
```json
{
  "city": "London",
  "country": "GB",
  "latitude": 51.5085,
  "longitude": -0.1257,
  "temperature": 15.2,
  "feelsLike": 14.8,
  "minTemp": 13.5,
  "maxTemp": 16.8,
  "humidity": 72,
  "pressure": 1013,
  "windSpeed": 4.5,
  "windDirection": 240,
  "description": "partly cloudy",
  "main": "Clouds",
  "icon": "02d",
  "visibility": 10000,
  "cloudiness": 40,
  "sunrise": "2024-07-19T05:30:00",
  "sunset": "2024-07-19T21:15:00",
  "timestamp": "2024-07-19T10:30:45"
}
```

### Forecast Response
```json
{
  "city": "Paris",
  "country": "France",
  "forecasts": [
    {
      "dateTime": 1721382600000,
      "temperature": 22.5,
      "feelsLike": 22.1,
      "humidity": 65,
      "description": "clear sky",
      "main": "Clear",
      "windSpeed": 3.2,
      "rainChance": 5.0
    },
    ...
  ]
}
```

## 🎨 Frontend Components

### Main Components
- **Dashboard** - Weather overview
- **SearchBar** - City search functionality
- **WeatherCard** - Current weather display
- **ForecastCard** - Forecast display
- **LocationDetector** - GPS integration
- **UnitToggle** - Celsius/Fahrenheit switch

### Features
- Real-time updates
- Weather charts
- Alert notifications
- Favorite cities
- Dark/Light theme

## 🔧 Configuration

### Backend Configuration (application-weather.yml)
```yaml
weather:
  api:
    key: your_openweathermap_api_key
    url: https://api.openweathermap.org/data/2.5

server:
  port: 8081
```

### Environment Variables
```bash
export WEATHER_API_KEY=your_api_key
export SPRING_PROFILES_ACTIVE=weather
```

## 📊 Weather Data Fields

| Field | Type | Description |
|-------|------|-------------|
| temperature | Double | Current temperature (°C) |
| feelsLike | Double | Feels-like temperature |
| minTemp/maxTemp | Double | Min/max temperatures |
| humidity | Integer | Humidity percentage (0-100) |
| pressure | Integer | Atmospheric pressure (hPa) |
| windSpeed | Double | Wind speed (m/s) |
| windDirection | Integer | Wind direction (0-360°) |
| cloudiness | Integer | Cloud cover percentage |
| visibility | Double | Visibility (meters) |
| sunrise/sunset | DateTime | Solar timing |

## 🚀 Eclipse 2025-06 Setup

1. **Import Project**
   - File → Import → Existing Maven Projects
   - Select project root
   - Click Finish

2. **Create Run Configuration**
   - Run → Run Configurations
   - Spring Boot App
   - Main class: `com.weather.WeatherDashboardApplication`
   - Arguments: `-Dspring.profiles.active=weather`

3. **Run Application**
   - Right-click project → Run As → Spring Boot App

## 🧪 Testing

### Test Weather API
```bash
# Get weather for London
curl http://localhost:8081/api/weather/city/London

# Get weather by coordinates
curl "http://localhost:8081/api/weather/coordinates?latitude=40.7128&longitude=-74.0060"

# Get forecast
curl http://localhost:8081/api/forecast/city/Paris

# Health check
curl http://localhost:8081/api/weather/health
```

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| API Key Invalid | Verify key at openweathermap.org dashboard |
| 401 Unauthorized | Check if API key is set correctly |
| City Not Found | Use full city name with country code |
| Connection Timeout | Ensure internet connection, check API status |
| Port Already in Use | Change port in application-weather.yml |
| CORS Error | Check CORS configuration in CorsConfig.java |

## 📝 Project Structure

```
weather-dashboard/
├── src/main/java/com/weather/
│   ├── config/
│   │   ├── CorsConfig.java
│   │   └── RestTemplateConfig.java
│   ├── controller/
│   │   ├── WeatherController.java
│   │   └── ForecastController.java
│   ├── dto/
│   │   ├── WeatherDTO.java
│   │   └── ForecastDTO.java
│   ├── model/
│   │   ├── WeatherData.java
│   │   └── ForecastData.java
│   ├── service/
│   │   ├── WeatherService.java
│   │   └── ForecastService.java
│   └── WeatherDashboardApplication.java
├── src/main/resources/
│   └── application-weather.yml
├── frontend/
│   ├── public/
│   ├── src/
│   ├── package.json
│   └── README.md
└── pom.xml
```

## 🔒 Security Notes

- Keep API key secure (use environment variables)
- Don't commit API keys to version control
- Use .env files for local development
- Implement rate limiting for production
- Add authentication for private endpoints

## 🌐 Deployment

### Docker Support
```dockerfile
FROM eclipse-temurin:21-jre
ENV WEATHER_API_KEY=your_key
COPY target/weather-dashboard-1.0.0.jar app.jar
ENTRYPOINT ["java", "-jar", "/app.jar", "--spring.profiles.active=weather"]
```

Build and run:
```bash
docker build -t weather-dashboard .
docker run -e WEATHER_API_KEY=your_key -p 8081:8081 weather-dashboard
```

## 🚀 Performance Tips

- Cache weather data (5-10 minutes)
- Use async/await for API calls
- Implement request throttling
- Compress API responses
- Use CDN for static assets

## 📚 API Documentation

Full OpenWeatherMap API docs: https://openweathermap.org/api

## 🎓 Learning Resources

- [Spring Boot Official Docs](https://spring.io/projects/spring-boot)
- [RestTemplate Guide](https://spring.io/guides/gs/consuming-rest)
- [React Documentation](https://react.dev)
- [Weather API Tutorial](https://openweathermap.org/guide)

## 🤝 Contributing

1. Fork the repository
2. Create feature branch
3. Make your changes
4. Submit pull request

## 📄 License

MIT License - Free to use and modify

## 🆘 Support

For issues:
1. Check troubleshooting section
2. Review API documentation
3. Check GitHub issues
4. Create detailed bug report

---

**Built with ❤️ for weather enthusiasts**

**Live Demo:** Coming Soon! 🚀

**Status:** ✅ Production Ready
