<template>
  <section class="exclusive-properties">
    <div class="container">
      <h2 class="section-title">Our Most Exclusive Properties</h2>
      <p class="section-description">Throughout our history, we've watched the markets rise, fall and evolve experience</p>
      
      <div class="menu-container">
        <button 
          v-for="category in categories" 
          :key="category"
          :class="['menu-button', { 'active': activeCategory === category }]"
          @click="setActiveCategory(category)"
        >
          {{ category }}
        </button>
      </div>
      
      <div class="properties-grid">
        <div 
          v-for="property in filteredProperties" 
          :key="property.id"
          class="property-card"
        >
          <div class="card-image" :style="{ backgroundImage: `url(${property.image})` }"></div>
          <div class="card-content">
                        <div class="card-features">
              <div class="feature-item">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
                  <path d="M6.66668 3.3335H3.33334V6.66683M3.33334 3.3335L7.50001 7.50016M13.3333 3.3335H16.6667V6.66683M16.6667 3.3335L12.5 7.50016M6.66668 16.6668H3.33334V13.3335M3.33334 16.6668L7.50001 12.5002M16.6667 16.6668L12.5 12.5002M13.3333 16.6668H16.6667V13.3335" stroke="#666666" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                <span>{{ property.sqft }}</span>
              </div>
              <div class="feature-item">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
                  <path d="M16.6667 8.3335H3.33335C2.89133 8.3335 2.4674 8.50909 2.15484 8.82165C1.84228 9.13421 1.66669 9.55814 1.66669 10.0002V16.6668M3.33335 8.3335V5.00016C3.33335 4.55814 3.50895 4.13421 3.82151 3.82165C4.13407 3.50909 4.55799 3.3335 5.00002 3.3335H15C15.442 3.3335 15.866 3.50909 16.1785 3.82165C16.4911 4.13421 16.6667 4.55814 16.6667 5.00016V8.3335M16.6667 8.3335C17.1087 8.3335 17.5326 8.50909 17.8452 8.82165C18.1578 9.13421 18.3334 9.55814 18.3334 10.0002V16.6668M10 3.3335V8.3335M1.66669 15.0002H18.3334" stroke="#666666" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                <span>{{ property.beds }} bed</span>
              </div>
              <div class="feature-item">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
                  <path d="M16.6667 8.3335H3.33335C2.89133 8.3335 2.4674 8.50909 2.15484 8.82165C1.84228 9.13421 1.66669 9.55814 1.66669 10.0002V16.6668M3.33335 8.3335V5.00016C3.33335 4.55814 3.50895 4.13421 3.82151 3.82165C4.13407 3.50909 4.55799 3.3335 5.00002 3.3335H15C15.442 3.3335 15.866 3.50909 16.1785 3.82165C16.4911 4.13421 16.6667 4.55814 16.6667 5.00016V8.3335M16.6667 8.3335C17.1087 8.3335 17.5326 8.50909 17.8452 8.82165C18.1578 9.13421 18.3334 9.55814 18.3334 10.0002V16.6668M10 3.3335V8.3335M1.66669 15.0002H18.3334" stroke="#666666" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                <span>{{ property.baths }} bath</span>
              </div>
            </div>
            <h3 class="card-title">{{ property.price }}</h3>
            <p class="card-description">{{ property.address }}</p>
          </div>
        </div>
      </div>
      
      <button class="bottom-button">
        Available Properties →
      </button>
    </div>
  </section>
</template>

<script>
import propertyImage from '../assets/property.png'

export default {
  name: 'ExclusiveProperties',
  data() {
    return {
      activeCategory: 'All',
      categories: [
        'All',
        'Villas',
        'Apartments',
        'Duplex Homes',
        'Urban Loft',
        'Coastal Retreat',
        'Penthouse',
        'Eco-Smart Home',
        'Urban Condos',
        'Historic Estates'
      ],
      properties: [
        {
          id: 1,
          price: '$1,250,000',
          address: '123 Sunset Boulevard, Miami',
          sqft: '3,500 sq ft',
          beds: 4,
          baths: 3,
          category: 'Villas',
          image: propertyImage
        },
        {
          id: 2,
          price: '$890,000',
          address: '456 Ocean Drive, California',
          sqft: '2,200 sq ft',
          beds: 3,
          baths: 2,
          category: 'Apartments',
          image: propertyImage
        },
        {
          id: 3,
          price: '$2,100,000',
          address: '789 Mountain View, Colorado',
          sqft: '4,800 sq ft',
          beds: 5,
          baths: 4,
          category: 'Duplex Homes',
          image: propertyImage
        },
        {
          id: 4,
          price: '$750,000',
          address: '321 Downtown Ave, New York',
          sqft: '1,800 sq ft',
          beds: 2,
          baths: 2,
          category: 'Urban Loft',
          image: propertyImage
        },
        {
          id: 5,
          price: '$1,800,000',
          address: '654 Beach Road, Florida',
          sqft: '3,200 sq ft',
          beds: 4,
          baths: 3,
          category: 'Coastal Retreat',
          image: propertyImage
        },
        {
          id: 6,
          price: '$3,500,000',
          address: '987 Skyline Tower, Chicago',
          sqft: '5,500 sq ft',
          beds: 6,
          baths: 5,
          category: 'Penthouse',
          image: propertyImage
        }
      ]
    }
  },
  computed: {
    filteredProperties() {
      if (this.activeCategory === 'All') {
        return this.properties
      }
      return this.properties.filter(property => property.category === this.activeCategory)
    }
  },
  methods: {
    setActiveCategory(category) {
      this.activeCategory = category
    }
  }
}
</script>

<style scoped>
.exclusive-properties {
  width: 100%;
  background: #FFF;
  padding: 100px 0;
}

.container {
  max-width: 1224px;
  margin: 0 auto;
  padding: 0 20px;
}

.section-title {
  color: var(--Text-Heading, #1E1E1E);
  text-align: center;
  font-family: "Noto Sans", sans-serif;
  font-size: 56px;
  font-style: normal;
  font-weight: 700;
  line-height: 64px;
  margin: 0 0 20px 0;
}

.section-description {
  color: var(--Text-Paragraph, #666);
  text-align: center;
  font-family: "Inter Tight", sans-serif;
  font-size: 20px;
  font-style: normal;
  font-weight: 400;
  line-height: 32px;
  margin: 0 0 60px 0;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.menu-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-bottom: 60px;
}

.menu-button {
  display: flex;
  padding: 8px 16px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
  border-radius: 8px;
  border: 1px solid var(--Border-Border, #E0E0E0);
  background: var(--Background-Pure-White, #FFF);
  color: var(--Text-Heading, #1E1E1E);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.menu-button:hover {
  border-color: var(--Text-Heading, #1E1E1E);
}

.menu-button.active {
  background: var(--Text-Heading, #1E1E1E);
  color: #FFF;
  border-color: var(--Text-Heading, #1E1E1E);
}

.properties-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
  margin-bottom: 60px;
}

.property-card {
  display: flex;
  width: 392px;
  flex-direction: column;
  align-items: flex-start;
  border-radius: 16px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  background: #FFF;
}

.property-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
}

.card-image {
  width: 392px;
  height: 294px;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 16px;
}

.card-content {
  text-align: left;
  width: 100%;
  padding: 24px 16px 16px 16px;
}

.card-title {
  color: #333;
  font-family: "Inter Tight", sans-serif;
  font-size: 24px;
  font-style: normal;
  font-weight: 500;
  line-height: 32px;
  margin: 0 0 8px 0;
}

.card-description {
  color: var(--Text-Title-2, #444);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px;
  margin: 0 0 16px 0;
}

.card-features {
  display: flex;
  gap: 16px;
  margin-bottom: 16px;
}

.feature-item {
  display: flex;
  align-items: center;
  gap: 4px;
}

.feature-item svg {
  flex-shrink: 0;
}

.feature-item span {
  color: var(--Text-Paragraph, #666);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px;
}

.bottom-button {
  display: flex;
  padding: 12px 40px;
  justify-content: center;
  align-items: center;
  gap: 8px;
  border-radius: 32px;
  background: var(--Text-Heading, #1E1E1E);
  border: none;
  color: #FFF;
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  margin: 0 auto;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.bottom-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

@media (max-width: 1200px) {
  .properties-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .properties-grid {
    grid-template-columns: 1fr;
  }
  
  .section-title {
    font-size: 40px;
    line-height: 48px;
  }
  
  .menu-container {
    gap: 8px;
  }
  
  .menu-button {
    padding: 6px 12px;
    font-size: 14px;
  }
}
</style>