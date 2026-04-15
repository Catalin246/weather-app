<script setup>
const currentWeather = {
  location: 'Amsterdam, NL',
  updatedAt: 'Updated 08:30',
  summary: 'Bright morning with a cool breeze off the water.',
  temperature: 16,
  feelsLike: 14,
  condition: 'Partly Cloudy',
  high: 19,
  low: 11,
  precipitation: '12%',
  humidity: '68%',
  wind: '18 km/h',
  uvIndex: '3 moderate',
}

const hourlyForecast = [
  { time: '09:00', temp: '16°', icon: '☀️' },
  { time: '12:00', temp: '18°', icon: '⛅' },
  { time: '15:00', temp: '19°', icon: '⛅' },
  { time: '18:00', temp: '17°', icon: '🌤️' },
  { time: '21:00', temp: '14°', icon: '🌙' },
]

const weeklyForecast = [
  { day: 'Wed', condition: 'Clouds', high: 19, low: 11 },
  { day: 'Thu', condition: 'Showers', high: 17, low: 10 },
  { day: 'Fri', condition: 'Sunny', high: 20, low: 12 },
  { day: 'Sat', condition: 'Windy', high: 18, low: 9 },
  { day: 'Sun', condition: 'Clear', high: 21, low: 13 },
]

const highlights = [
  {
    label: 'Rain chance',
    value: '12%',
    detail: 'Low risk through the afternoon commute.',
  },
  {
    label: 'Air quality',
    value: '42 AQI',
    detail: 'Comfortable conditions for outdoor plans.',
  },
  {
    label: 'Sunset',
    value: '20:31',
    detail: 'Golden light peaks around canal hour.',
  },
]
</script>

<template>
  <main class="dashboard-shell">
    <section class="hero-card">
      <div class="hero-copy">
        <p class="eyebrow">Weather dashboard</p>
        <h1>{{ currentWeather.location }}</h1>
        <p class="hero-summary">{{ currentWeather.summary }}</p>
        <div class="hero-meta">
          <span>{{ currentWeather.updatedAt }}</span>
          <span>{{ currentWeather.condition }}</span>
        </div>
      </div>

      <div class="hero-temp">
        <div class="temp-mark">{{ currentWeather.temperature }}°</div>
        <p>Feels like {{ currentWeather.feelsLike }}°</p>
        <p>H: {{ currentWeather.high }}° / L: {{ currentWeather.low }}°</p>
      </div>
    </section>

    <section class="stats-grid">
      <article class="panel">
        <div class="panel-heading">
          <h2>Today</h2>
          <span>Now</span>
        </div>
        <div class="metric-list">
          <div>
            <span>Precipitation</span>
            <strong>{{ currentWeather.precipitation }}</strong>
          </div>
          <div>
            <span>Humidity</span>
            <strong>{{ currentWeather.humidity }}</strong>
          </div>
          <div>
            <span>Wind</span>
            <strong>{{ currentWeather.wind }}</strong>
          </div>
          <div>
            <span>UV Index</span>
            <strong>{{ currentWeather.uvIndex }}</strong>
          </div>
        </div>
      </article>

      <article class="panel">
        <div class="panel-heading">
          <h2>Hourly forecast</h2>
          <span>Next 12 hours</span>
        </div>
        <div class="hourly-row">
          <div v-for="item in hourlyForecast" :key="item.time" class="hour-chip">
            <span>{{ item.time }}</span>
            <strong>{{ item.icon }}</strong>
            <span>{{ item.temp }}</span>
          </div>
        </div>
      </article>
    </section>

    <section class="lower-grid">
      <article class="panel">
        <div class="panel-heading">
          <h2>5-day outlook</h2>
          <span>Static sample data</span>
        </div>
        <div class="forecast-list">
          <div v-for="item in weeklyForecast" :key="item.day" class="forecast-row">
            <strong>{{ item.day }}</strong>
            <span>{{ item.condition }}</span>
            <span>{{ item.high }}° / {{ item.low }}°</span>
          </div>
        </div>
      </article>

      <article class="panel highlights-panel">
        <div class="panel-heading">
          <h2>Highlights</h2>
          <span>At a glance</span>
        </div>
        <div class="highlight-list">
          <div v-for="item in highlights" :key="item.label" class="highlight-card">
            <span>{{ item.label }}</span>
            <strong>{{ item.value }}</strong>
            <p>{{ item.detail }}</p>
          </div>
        </div>
      </article>
    </section>
  </main>
</template>
