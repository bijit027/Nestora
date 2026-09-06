<template>
  <div class="app" :style="{ backgroundImage: `url(${nestoraBg})` }">
    <nav class="navbar">
      <div class="nav-content">
        <div class="nav-left">
          <div class="logo">NESTORA</div>
        </div>
          <div class="nav-links">
            <a 
              v-for="link in navLinks" 
              :key="link.name"
              :class="['nav-link', { 'active': activeLink === link.name }]"
              @click="setActiveLink(link.name)"
            >
              {{ link.name }}
            </a>
          </div>
        <div class="nav-right">

          <button class="contact-button">Contact</button>
        </div>
      </div>
    </nav>

    <main class="hero-section">
      <div class="hero-content">
        <h1 class="hero-title">Nestora property</h1>
        <p class="hero-description">Throughout our history, we've watched the markets rise, fall and evolve – shaping the experience that guides our current investment philosophy.</p>
        <button class="action-button">
          Available Properties
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path d="M3 12.013L20.789 12M14.013 19L21 12L14.012 5" stroke="#1E1E1E" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
        <div class="scroll-indicator">
          <div class="scroll-icon">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 5V19M12 19L5 12M12 19L19 12" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </div>
        </div>
      </div>
    </main>

    <section class="featured-section">
      <div class="featured-background">
        <h2 class="featured-header">Our Featured Properties</h2>
        <p class="featured-description">Throughout our history, we've watched the markets rise, fall and evolve – shaping the experience that guides our current investment philosophy.</p>
        
        <div class="carousel-container">
          <div class="carousel">
            <div 
              v-for="(property, index) in properties" 
              :key="index"
              :class="['property-card', getCardClass(index)]"
              :style="getCardStyle(index)"
            >
              <div class="card-image" :style="{ backgroundColor: property.color }">
                <div class="card-content">
                  <h3 class="card-title">{{ property.title }}</h3>
                  <p class="card-location">{{ property.location }}</p>
                  <p class="card-price">{{ property.price }}</p>
                  <div v-if="index === activeIndex" class="card-details">
                    <span>{{ property.sqft }}</span>
                    <span>{{ property.beds }} Beds</span>
                    <span>{{ property.baths }} Baths</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="carousel-navigation">
          <button class="nav-btn prev-btn" @click="prevSlide">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <path d="M15 18L9 12L15 6" stroke="#333" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
          <button class="nav-btn next-btn" @click="nextSlide">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
              <path d="M9 18L15 12L9 6" stroke="#FFF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </div>
      </div>
    </section>

    <ExclusiveProperties />
    <JourneySection />
  </div>
</template>

<script>
import ExclusiveProperties from './components/ExclusiveProperties.vue'
import nestoraBg from './assets/nestora.png'
import JourneySection from './components/journeySection.vue'

export default {
  name: 'App',
  components: {
    ExclusiveProperties,
    JourneySection
  },
  data() {
    return {
      activeLink: 'Home',
      navLinks: [
        { name: 'Home' },
        { name: 'Properties' },
        { name: 'About' },
        { name: 'Agent' },
        { name: 'Blog' }
      ],
      activeIndex: 2,
      properties: [
        { title: 'Luxury Villa', location: 'Miami, Florida', price: '$5,80,000', color: '#FF6B6B', sqft: '2,500 sqft', beds: 4, baths: 3 },
        { title: 'Modern Home', location: 'Seattle, Washington', price: '$4,50,000', color: '#4ECDC4', sqft: '2,200 sqft', beds: 3, baths: 2 },
        { title: 'Beach House', location: 'California', price: '$6,20,000', color: '#45B7D1', sqft: '2,800 sqft', beds: 5, baths: 4 },
        { title: 'City Apartment', location: 'New York', price: '$3,80,000', color: '#96CEB4', sqft: '1,800 sqft', beds: 2, baths: 2 },
        { title: 'Mountain Retreat', location: 'Colorado', price: '$7,50,000', color: '#FFEAA7', sqft: '3,200 sqft', beds: 6, baths: 5 }
      ],
      nestoraBg
    }
  },
  methods: {
    setActiveLink(linkName) {
      this.activeLink = linkName
    },
    getCardClass(index) {
      const totalCards = this.properties.length
      const centerIndex = this.activeIndex
      
      // Calculate circular distance
      let distance = index - centerIndex
      
      // Handle circular wrapping
      if (distance > totalCards / 2) {
        distance -= totalCards
      } else if (distance < -totalCards / 2) {
        distance += totalCards
      }
      
      const absDistance = Math.abs(distance)
      
      if (absDistance === 0) return 'active'
      if (absDistance === 1) return 'medium'
      if (absDistance === 2) return 'small'
      return 'tiny'
    },
    getCardStyle(index) {
      const totalCards = this.properties.length
      const centerIndex = this.activeIndex
      
      // Calculate circular distance to ensure 2 cards on each side
      let distance = index - centerIndex
      
      // Handle circular wrapping
      if (distance > totalCards / 2) {
        distance -= totalCards
      } else if (distance < -totalCards / 2) {
        distance += totalCards
      }
      
      const absDistance = Math.abs(distance)
      
      let width, height, zIndex, scale, opacity, offsetX
      
      if (absDistance === 0) {
        // Center card (largest)
        width = '288px'
        height = '513px'
        zIndex = 5
        scale = 1
        opacity = 1
        offsetX = 0
      } else if (absDistance === 1) {
        // Second largest cards (immediate neighbors)
        width = '230px'
        height = '410px'
        zIndex = 4
        scale = 0.8
        opacity = 0.95
        // Calculate offset with 24px gap between scaled cards
        // Center card half width (scaled): 288px * 1 / 2 = 144px
        // Gap: 24px
        // Medium card half width (scaled): 230px * 0.8 / 2 = 92px
        // Total offset: 144px + 24px + 92px = 260px
        offsetX = distance > 0 ? 260 : -260
      } else if (absDistance === 2) {
        // Smallest cards (second neighbors)
        width = '184px'
        height = '328px'
        zIndex = 3
        scale = 0.65
        opacity = 0.85
        // Calculate offset with 24px gaps between scaled cards
        // Center card half width (scaled): 288px * 1 / 2 = 144px
        // Gap 1: 24px
        // Medium card full width (scaled): 230px * 0.8 = 184px
        // Gap 2: 24px
        // Small card half width (scaled): 184px * 0.65 / 2 = 59.8px ≈ 60px
        // Total offset: 144px + 24px + 184px + 24px + 60px = 436px
        offsetX = distance > 0 ? 436 : -436
      } else {
        // Cards further away (not visible in normal state)
        width = '150px'
        height = '267px'
        zIndex = 1
        scale = 0.4
        opacity = 0
        offsetX = distance > 0 ? 400 : -400
      }
      
      return {
        width,
        height,
        zIndex,
        transform: `translateX(${offsetX}px) scale(${scale})`,
        opacity
      }
    },
    nextSlide() {
      this.activeIndex = (this.activeIndex + 1) % this.properties.length
    },
    prevSlide() {
      this.activeIndex = (this.activeIndex - 1 + this.properties.length) % this.properties.length
    }
  }
}
</script>

<style scoped>
.app {
  width: 100%;
  min-height: 100vh;
  background-size: contain;
  background-position: center top;
  background-repeat: no-repeat;
  position: relative;
}

.navbar {
  position: relative;
  padding: 20px 0;
}

.nav-content {
  display: flex;
  width: 1224px;
  padding: 12px 16px;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  border-radius: 48px;
  background: rgba(255, 255, 255, 0.20);
  backdrop-filter: blur(8px);
}

.logo {
  color: #FFF;
  font-family: "Noto Sans", sans-serif;
  font-size: 24px;
  font-weight: 700;
  letter-spacing: 1px;
}

.nav-right {
  display: flex;
  align-items: center;
  gap: 40px;
}

.nav-links {
  display: flex;
  gap: 32px;
  align-items: center;
}

.nav-link {
  color: #FFF;
  font-family: "Noto Sans", sans-serif;
  font-size: 16px;
  font-weight: 500;
  text-decoration: none;
  cursor: pointer;
  transition: color 0.3s ease;
  padding: 8px 12px;
  border-radius: 8px;
}

.nav-link:hover {
  color: rgba(255, 255, 255, 0.8);
}

.nav-link.active {
  color: rgba(255, 255, 255, 0.9);
  font-weight: 600;
}

.contact-button {
  display: flex;
  padding: 12px 32px;
  justify-content: center;
  align-items: center;
  border-radius: 48px;
  background: #FFF;
  border: none;
  color: #3b82f6;
  font-family: "Noto Sans", sans-serif;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.contact-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.hero-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  max-width: 1224px;
  height: 700px;
  margin: 0 auto;
  box-sizing: border-box;
  position: relative;
}

.hero-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0;
}

.hero-title {
  color: var(--Background-Pure-White, #FFF);
  font-family: "Noto Sans", sans-serif;
  font-size: 110px;
  font-style: normal;
  font-weight: 700;
  line-height: 112px;
  letter-spacing: 2.4px;
  text-transform: uppercase;
  margin: 0;
}

.hero-description {
  color: var(--Background-Pure-White, #FFF);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px;
  margin: 24px 0 40px 0;
  max-width: 392px;
}

.action-button {
  display: flex;
  padding: 12px 40px;
  justify-content: center;
  align-items: center;
  gap: 8px;
  border-radius: 32px;
  background: var(--Background-Pure-White, #FFF);
  border: none;
  color: var(--Text-Heading, #1E1E1E);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px;
  cursor: pointer;
  margin-top: 0;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.action-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.scroll-indicator {
  margin-top: 60px;
  display: flex;
  justify-content: flex-end;
  width: 100%;
}

.scroll-icon {
  width: 80px;
  height: 80px;
  border-radius: 57.497px;
  border: 1px solid rgba(255, 255, 255, 0.40);
  background: rgba(255, 255, 255, 0.20);
  backdrop-filter: blur(8px);
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition: background 0.3s ease;
}

.scroll-icon:hover {
  background: rgba(255, 255, 255, 0.30);
}

.featured-section {
  position: relative;
  width: 100%;
  min-height: 100vh;
  background: #FFF;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 200px 0 100px 0;
  overflow: visible;
}

.featured-background {
  width: 636px;
  height: 848px;
  aspect-ratio: 3/4;
  position: relative;
  border-radius: 24px;
  background: var(--Primary-Color, #EDF7FF);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 60px 40px 40px 40px;
  box-sizing: border-box;
  overflow: visible;
}

.featured-header {
  color: var(--Text-Heading, #1E1E1E);
  text-align: center;
  font-family: "Noto Sans", sans-serif;
  font-size: 40px;
  font-style: normal;
  font-weight: 700;
  line-height: 48px;
  margin: 0 0 20px 0;
}

.featured-description {
  color: var(--Text-Paragraph, #666);
  text-align: center;
  font-family: "Inter Tight", sans-serif;
  font-size: 20px;
  font-style: normal;
  font-weight: 400;
  line-height: 32px;
  margin: 0 0 60px 0;
  max-width: 500px;
}

.carousel-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  position: relative;
  z-index: 10;
}

.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 480px;
  width: 100%;
  position: relative;
  overflow: visible;
  z-index: 10;
}

.property-card {
  position: absolute;
  transition: all 0.5s ease;
  border-radius: 16px;
  overflow: hidden;
  cursor: pointer;
}

.card-image {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  padding: 20px;
  box-sizing: border-box;
  border-radius: 16px;
}

.card-content {
  text-align: center;
}

.card-title {
  color: var(--Background-Pure-White, #FFF);
  text-align: center;
  font-family: "Inter Tight", sans-serif;
  font-size: 24px;
  font-style: normal;
  font-weight: 500;
  line-height: 32px;
  margin: 0 0 8px 0;
}

.card-location {
  color: var(--Background-Pure-White, #FFF);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-weight: 400;
  margin: 0 0 4px 0;
}

.card-price {
  color: var(--Background-Pure-White, #FFF);
  font-family: "Inter Tight", sans-serif;
  font-size: 20px;
  font-weight: 600;
  margin: 0 0 12px 0;
}

.card-details {
  display: flex;
  justify-content: center;
  gap: 16px;
  margin-top: 12px;
}

.card-details span {
  color: var(--Background-Pure-White, #FFF);
  font-family: "Inter Tight", sans-serif;
  font-size: 14px;
  font-weight: 400;
}

.property-card:not(.active) .card-details {
  display: none;
}

.property-card.small .card-price {
  font-size: 16px;
}

.property-card.small .card-title {
  font-size: 18px;
}

.property-card.small .card-location {
  font-size: 12px;
}

.property-card.tiny {
  opacity: 0 !important;
  pointer-events: none;
}

.carousel-navigation {
  margin-top: auto;
  margin-top: 40px;
  display: flex;
  gap: 20px;
}

.nav-btn {
  display: flex;
  width: 32px;
  height: 32px;
  padding: 8px;
  justify-content: center;
  align-items: center;
  aspect-ratio: 1/1;
  border-radius: 132px;
  border: none;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.prev-btn {
  background: #FFF;
}

.next-btn {
  background: var(--Text-Title-1, #333);
}

.nav-btn:hover {
  transform: scale(1.1);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.property-card.active {
  z-index: 5 !important;
}

.property-card.medium {
  z-index: 4 !important;
}

.property-card.small {
  z-index: 3 !important;
}

.property-card.tiny {
  z-index: 2 !important;
}
</style>