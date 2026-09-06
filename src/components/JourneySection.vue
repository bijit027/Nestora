<template>
  <section class="journey-section">
    <div class="journey-left">
      <div class="image-wrapper left-image">
        <!-- Make sure left.png is in your assets directory -->
        <img src="../assets/left.png" alt="Left" />
      </div>
      <div class="image-wrapper right-image">
        <!-- Make sure right.png is in your assets directory -->
        <img src="../assets/right.png" alt="Right" />
      </div>
      
      <div class="experience-circle">
        <div class="circle-inner">
          <svg viewBox="0 0 131 131" class="circle-text">
            <path id="curve" d="M 65.5, 65.5 m -60, 0 a 60,60 0 1,1 120,0 a 60,60 0 1,1 -120,0" fill="transparent" />
            <text>
              <textPath href="#curve" startOffset="50%" text-anchor="middle" font-size="11" font-family="'Inter Tight', sans-serif" font-weight="500" letter-spacing="3">
                YEARS OF EXPERIENCE
              </textPath>
            </text>
          </svg>
          <span class="circle-number">12</span>
        </div>
      </div>
      
      <div class="stats-card">
        <div class="stats-header">
          <span class="stats-number">1,200 +</span>
          <span class="stats-title">Property Closing</span>
        </div>
        <p class="stats-desc">We help you sell your property with confidence through expert strategy</p>
      </div>
    </div>
    
    <div class="journey-right">
      <h2 class="section-title">Our Journey Toward<br>Excellence</h2>
      <div class="section-desc">
        <p>We believe every good deal is founded on a great partnership. Our partnerships are built on trust, honesty and committed collaboration – many of them standing strong for decades. Championing transparency,</p>
        <p>We deliver on our promises and remain reachable 24/7.</p>
      </div>
      <button class="learn-more-btn">
        Learn More
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M5 12H19M19 12L12 5M19 12L12 19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
    </div>
  </section>
</template>
<script>
export default {
  name: 'JourneySection',
};
</script>
<style scoped>
.journey-section {
  display: flex;
  gap: 24px;
  align-items: center;
  max-width: 1224px;
  margin: 0 auto;
}
/* Left Column Styles */
.journey-left {
  flex: 1;
  position: relative;
  min-height: 620px; /* Increased height to accommodate the layout */
  width: 100%;
}

.image-wrapper {
  background-color: #f0f0f0;
  border-radius: 16px;
  overflow: hidden;
  position: absolute;
}

.image-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.left-image {
  width: 288px;
  height: 512px;
  left: 0;
  bottom: 0;
  z-index: 1;
}

.right-image {
  width: 288px;
  height: 244px;
  right: 10px;
  top: 105px;
  z-index: 1;
}

/* Circle Styles */
.experience-circle {
  position: absolute;
  left: 180px;
  top: 180px;
  width: 243px;
  height: 243px;
  padding: 28px;
  flex-shrink: 0;
  border-radius: 168px;
  background: #FFF;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
}

.circle-inner {
  position: relative;
  width: 131px;
  height: 131px;
  display: flex;
  align-items: center;
  justify-content: center;
  fill: var(--Text-Heading, #1E1E1E);
}

.circle-text {
  position: absolute;
  width: 100%;
  height: 100%;
  transform: rotate(-90deg); /* Adjust text starting position */
}

.circle-number {
  color: var(--Text-Heading, #1E1E1E);
  font-family: "Noto Sans", sans-serif;
  font-size: 40px;
  font-style: normal;
  font-weight: 700;
  line-height: 48px; /* 120% */
  text-transform: capitalize;
}

/* Stats Card Styles */
.stats-card {
  position: absolute;
  right: 10px;
  bottom: 0;
  display: flex;
  width: 288px;
  height: 244px;
  padding: 24px 16px;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-start;
  gap: 16px;
  background: #FFF;
  border-radius: 16px;
  border: 1px solid #EBEBEB;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.05);
  z-index: 5;
  box-sizing: border-box;
}
.stats-header {
  display: flex;
  align-items: baseline;
  gap: 8px;
}
.stats-number {
  color: var(--Text-Heading, #1E1E1E);
  font-family: "Inter Tight", sans-serif;
  font-size: 24px;
  font-style: normal;
  font-weight: 700;
}
.stats-title {
  color: var(--Text-Title-1, #333);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 500;
  line-height: 24px; /* 150% */
}
.stats-desc {
  color: var(--Text-Paragraph, #666);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px; /* 150% */
  margin: 0;
}
/* Right Column Styles */
.journey-right {
  flex: 1;
}
.section-title {
  color: var(--Text-Heading, #1E1E1E);
  font-family: "Noto Sans", sans-serif;
  font-size: 40px;
  font-style: normal;
  font-weight: 700;
  line-height: 48px; /* 120% */
  margin-top: 0;
  margin-bottom: 24px;
}
.section-desc {
  color: var(--Text-Paragraph, #666);
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 24px; /* 150% */
  margin-bottom: 40px;
}
.section-desc p {
  margin-bottom: 16px;
}
.section-desc p:last-child {
  margin-bottom: 0;
}
.learn-more-btn {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  padding: 16px 32px;
  background-color: #1a1a1a;
  color: #ffffff;
  border: none;
  border-radius: 40px;
  font-family: "Inter Tight", sans-serif;
  font-size: 16px;
  font-weight: 700;
  line-height: 32px; /* 133.333% */
  cursor: pointer;
  transition: background-color 0.2s ease, transform 0.2s ease;
}
.learn-more-btn:hover {
  background-color: #333333;
  transform: translateY(-2px);
}
</style>