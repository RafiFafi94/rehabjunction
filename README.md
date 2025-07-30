<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Rehab Junction</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500;700&display=swap" rel="stylesheet" />
  <style>
    body {
      margin: 0;
      font-family: 'Montserrat', sans-serif;
      background: #f9f9f9;
      color: #333;
      max-width: 1400px;
      margin-left: auto;
      margin-right: auto;
      scroll-behavior: smooth; /* smooth scrolling */
    }
    header {
      background: #0d253f;
      color: #fff;
      padding: 1.5rem 2rem;
      text-align: center;
    }
    header h1 {
      margin: 0;
      font-size: 2.2rem;
    }
    nav {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 2rem;
      margin-top: 1rem;
    }
    nav a {
      color: #fff;
      text-decoration: none;
      font-weight: 500;
    }
    nav a:hover {
      text-decoration: underline;
    }
    .book-btn {
      background: #ff9800;
      color: white;
      padding: 0.6rem 1.2rem;
      border-radius: 8px;
      font-weight: 600;
      text-decoration: none;
      transition: background 0.3s ease;
    }
    .book-btn:hover {
      background: #e68900;
    }
    /* Hero section */
    .hero {
      position: relative;
      color: white;
      text-align: center;
      padding: 6rem 2rem;
      overflow: hidden;
    }
    .hero img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      z-index: -1;
      filter: brightness(0.6);
    }
    .hero h2 {
      font-size: 2.5rem;
      margin: 0;
      position: relative;
      z-index: 1;
    }
    .hero p {
      font-size: 1.2rem;
      margin-top: 1rem;
      position: relative;
      z-index: 1;
    }
    section {
      padding: 3rem 2rem;
      max-width: 1100px;
      margin: auto;
    }
    .about-card {
      background: white;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
    }
    .about-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    }
    footer {
      background: #0d253f;
      color: white;
      text-align: center;
      padding: 2rem;
    }
    footer p {
      margin: .5rem 0;
    }
    /* Testimonials */
    #testimonials {
      background: #ffffff;
      padding: 60px 20px;
    }
    .testimonial-container {
      max-width: 1200px;
      margin: auto;
      overflow: hidden;
      position: relative;
    }
    .testimonial-slider {
      display: flex;
      /* Removed transition because animation handles movement */
      will-change: transform;
      animation: slideLeft 30s linear infinite;
    }
    .testimonial {
      flex: 0 0 33.3333%;
      box-sizing: border-box;
      padding: 20px;
      text-align: center;
      border: 1px solid #ddd;
      margin: 0 10px;
      border-radius: 10px;
      background-color: #f8f8f8;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    .testimonial p {
      font-size: 1.1rem;
      line-height: 1.6;
      color: #333;
      font-style: italic;
      margin: 0 auto 15px auto;
      max-width: 90%;
      min-height: 90px;
    }
    .testimonial h4 {
      margin-top: 0;
      color: #0073e6;
      font-weight: 600;
    }
    @media (max-width: 900px) {
      .testimonial {
        flex: 0 0 50%;
      }
    }
    @media (max-width: 600px) {
      .testimonial {
        flex: 0 0 100%;
        margin: 0 0 20px 0;
      }
    }
    /* Services */
    .service-card {
      background: white;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      cursor: pointer;
      transition: transform 0.3s;
    }
    .service-card:hover {
      transform: scale(1.02);
    }
    .service-header {
      height: 120px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      text-align: center;
    }
    .service-header h3 {
      font-size: 1.2rem;
      margin: 0;
    }
    .gradient1 { background: linear-gradient(135deg, #003366, #0055aa); }
    .gradient2 { background: linear-gradient(135deg, #006633, #00aa55); }
    .gradient3 { background: linear-gradient(135deg, #660033, #aa0055); }
    .gradient4 { background: linear-gradient(135deg, #884400, #cc6600); }
    .gradient5 { background: linear-gradient(135deg, #444444, #777777); }
    .gradient6 { background: linear-gradient(135deg, #663399, #9966cc); }
    .service-desc {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.5s ease, padding 0.3s ease;
      padding: 0 20px;
      line-height: 1.6;
      color: #333;
    }
    .service-desc.open {
      max-height: 500px;
      padding: 20px;
    }
    #about > div > div:nth-child(3) > div {
      display: flex !important;
      flex-wrap: nowrap !important;
      justify-content: center;
      gap: 30px !important;
      max-width: none !important;
    }
    .about-card {
      min-width: 250px;
      max-width: 280px;
    }

    @keyframes slideLeft {
      0% {
        transform: translateX(0);
      }
      100% {
        transform: translateX(-50%);
      }
    }
  </style>
  <script>
    function toggleService(id) {
      document.querySelectorAll(".service-desc").forEach(desc => {
        if (desc.id === id) {
          desc.classList.toggle("open");
        } else {
          desc.classList.remove("open");
        }
      });
    }
  </script>
</head>
<body>
  
  <header>
    <h1>Rehab Junction</h1>
    <nav>
      <a href="#about">About</a>
      <a href="#services">Services</a>
      <a href="#contact">Contact</a>
      <a href="https://docs.google.com/forms/d/e/1FAIpQLSd1kQ5VM66o6n_uBrt66WEQNSFvCiTFccxM7XpMcNCYByiTWA/viewform?embedded=true" target="_blank" class="book-btn">
        Book Now
      </a>
    </nav>
  </header>
  
  <!-- Hero Section -->
  <section class="hero">
    <img src="https://images.unsplash.com/photo-1605296867304-46d5465a13f1?fit=crop&w=1600&q=80" alt="Rehab therapy" loading="lazy" />
    <h2>Your Path to Recovery Starts Here</h2>
    <p>Professional rehabilitation and massage therapy tailored to your needs.</p>
  </section>

  <section id="about" style="padding: 60px 20px; background: #f4f7fb;">
  <div style="max-width: 1000px; margin: auto; text-align: center;">
    <h2 style="font-size: 2.2rem; margin-bottom: 20px; color: #003366;">About Rehab Junction</h2>
    <p style="font-size: 1.1rem; line-height: 1.8; margin-bottom: 30px; color: #333;">
      At <strong>Rehab Junction</strong>, we are dedicated to helping you regain movement, reduce pain, and 
      achieve lasting recovery. Offering both <strong>mobile services</strong> in the comfort of your home 
      and <strong>treatments at our office</strong>, we provide flexibility and expert care tailored to your needs.
    </p>

    <p style="font-size: 1.1rem; line-height: 1.8; margin-bottom: 40px; color: #333;">
      Whether you’re recovering from a sports injury, dealing with chronic pain, or simply want to 
      improve your overall wellbeing, we create personalised programs designed to help you 
      move better, feel stronger, and live without limitations.
    </p>

    <!-- Why Choose Us Section -->
 <section id="about" style="padding: 60px 20px; background: #f4f7fb;">
  <div style="max-width: 1200px; margin: auto; text-align: center;">
    <h2 style="font-size: 2.2rem; margin-bottom: 20px; color: #003366;">Why Choose Rehab Junction?</h2>
    <p style="font-size: 1.1rem; line-height: 1.8; margin-bottom: 40px; color: #333;">
      Discover what sets us apart and why our clients trust us to guide their journey to recovery:
    </p>

    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 30px;">

      <div style="display: flex; gap: 30px; flex-wrap: nowrap; justify-content: center;">
  <!-- Feature 1 -->
  <div class="about-card" style="background: white; padding: 25px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <img src="https://img.icons8.com/color/96/ambulance.png" alt="Mobile Care" style="width:70px; margin-bottom:15px;">
    <h3 style="color: #0073e6;">Mobile & In-Office Care</h3>
    <p style="margin-top:15px; color:#555; font-size:0.95rem; line-height:1.6;">
      Receive professional rehabilitation in your own home or visit us at our fully equipped office.
    </p>
  </div>
  
  <!-- Feature 2 -->
  <div class="about-card" style="background: white; padding: 25px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <img src="https://img.icons8.com/color/96/task.png" alt="Treatment Plans" style="width:70px; margin-bottom:15px;">
    <h3 style="color: #0073e6;">Personalised Plans</h3>
    <p style="margin-top:15px; color:#555; font-size:0.95rem; line-height:1.6;">
      Every treatment is tailored to your specific goals, ensuring the best and fastest recovery.
    </p>
  </div>
  
  <!-- Feature 3 -->
  <div class="about-card" style="background: white; padding: 25px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <img src="https://img.icons8.com/color/96/microscope.png" alt="Evidence Based" style="width:70px; margin-bottom:15px;">
    <h3 style="color: #0073e6;">Evidence-Based Techniques</h3>
    <p style="margin-top:15px; color:#555; font-size:0.95rem; line-height:1.6;">
      We use proven rehabilitation and therapy methods backed by clinical research.
    </p>
  </div>
  
  <!-- Feature 4 -->
  <div class="about-card" style="background: white; padding: 25px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <img src="https://img.icons8.com/color/96/dumbbell.png" alt="Recovery" style="width:70px; margin-bottom:15px;">
    <h3 style="color: #0073e6;">Focus on Long-Term Recovery</h3>
    <p style="margin-top:15px; color:#555; font-size:0.95rem; line-height:1.6;">
      Our goal is not just short-term relief but lasting improvements in your health and mobility.
    </p>
  </div>
</div>


    </div>
  </div>
</section>


<style>
  .about-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
  }
</style>


<style>
  .about-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
  }
</style>


  
<!-- Services Section -->
<section id="services" class="services" style="padding: 40px; background: #f9f9f9;">
  <h2 style="text-align: center; margin-bottom: 30px; color: #003366;">Our Services</h2>

  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px;">

    <!-- Service 1 -->
    <div class="service-card" onclick="toggleService('massage')">
      <div class="service-header gradient1">
        <h3>Sports Massage</h3>
      </div>
      <div id="massage" class="service-desc">
        <p>Our sports massage therapy targets muscles, ligaments, and tendons to alleviate pain, enhance blood flow, and accelerate healing. Using advanced techniques, we focus on reducing muscular tension and promoting overall physical recovery.</p>
        <strong>Key Benefits:</strong>
        <ul>
          <li>Effective pain and muscle tension relief</li>
          <li>Enhanced circulation and nutrient delivery</li>
          <li>Accelerated recovery from athletic exertion</li>
          <li>Improved relaxation and stress management</li>
        </ul>
      </div>
    </div>

    <!-- Service 2 -->
    <div class="service-card" onclick="toggleService('therapy')">
      <div class="service-header gradient2">
        <h3>Sports Therapy</h3>
      </div>
      <div id="therapy" class="service-desc">
        <p>Our sports therapy program combines evidence-based techniques such as trigger point therapy and soft tissue mobilisation to effectively treat musculoskeletal injuries, reduce pain, and restore function, tailored to each athlete’s needs.</p>
        <strong>Conditions Treated:</strong>
        <ul>
          <li>Muscle strains and tears</li>
          <li>Repetitive strain injuries</li>
          <li>Joint stiffness and mobility limitations</li>
          <li>Comprehensive pain management</li>
        </ul>
      </div>
    </div>

    <!-- Service 3 -->
    <div class="service-card" onclick="toggleService('spinal')">
      <div class="service-header gradient3">
        <h3>Spinal Joint Mobilisation</h3>
      </div>
      <div id="spinal" class="service-desc">
        <p>Using precise mobilisation and manipulation techniques, we restore optimal joint movement, reduce stiffness, and alleviate spinal discomfort. This service improves flexibility, enhances neuromuscular function, and supports long-term spinal health.</p>
      </div>
    </div>

    <!-- Service 4 -->
    <div class="service-card" onclick="toggleService('assessment')">
      <div class="service-header gradient4">
        <h3>Clinical Joint Assessment</h3>
      </div>
      <div id="assessment" class="service-desc">
        <p>Our comprehensive clinical joint assessment evaluates joint movement, strength, and ligament integrity using advanced diagnostic tools to identify underlying issues, enabling us to develop personalized, targeted treatment plans.</p>
      </div>
    </div>

    <!-- Service 5 -->
    <div class="service-card" onclick="toggleService('rehab')">
      <div class="service-header gradient5">
        <h3>Injury Rehabilitation</h3>
      </div>
      <div id="rehab" class="service-desc">
        <p>We offer structured rehabilitation programs designed to promote healing, restore mobility, and strengthen injured areas. Our multidisciplinary approach focuses on pain management, functional recovery, and preventing future injury.</p>
        <strong>Program Highlights:</strong>
        <ul>
          <li>Accelerated return to athletic performance</li>
          <li>Reduction of pain and inflammation</li>
          <li>Enhanced flexibility, balance, and coordination</li>
          <li>Individually tailored rehabilitation plans</li>
        </ul>
      </div>
    </div>

    <!-- Service 6 -->
    <div class="service-card" onclick="toggleService('exercise')">
      <div class="service-header gradient6">
        <h3>Exercise Therapy</h3>
      </div>
      <div id="exercise" class="service-desc">
        <p>Our personalized exercise therapy programs combine strength training, flexibility exercises, balance improvement, and sport-specific drills to optimize performance, prevent injury, and support long-term musculoskeletal health.</p>
      </div>
    </div>

  </div>
</section>

<style>
  .service-card {
    background: white;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    cursor: pointer;
    transition: transform 0.3s;
  }
  .service-card:hover {
    transform: scale(1.02);
  }

  .service-header {
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    text-align: center;
  }

  .service-header h3 {
    font-size: 1.2rem;
    margin: 0;
  }

  /* Different Gradient Colors */
  .gradient1 { background: linear-gradient(135deg, #003366, #0055aa); }
  .gradient2 { background: linear-gradient(135deg, #006633, #00aa55); }
  .gradient3 { background: linear-gradient(135deg, #660033, #aa0055); }
  .gradient4 { background: linear-gradient(135deg, #884400, #cc6600); }
  .gradient5 { background: linear-gradient(135deg, #444444, #777777); }
  .gradient6 { background: linear-gradient(135deg, #663399, #9966cc); }

  .service-desc {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.5s ease, padding 0.3s ease;
    padding: 0 20px;
    line-height: 1.6;
    color: #333;
  }

  .service-desc.open {
    max-height: 700px;
    padding: 20px;
  }
</style>

<script>
  function toggleService(id) {
    document.querySelectorAll(".service-desc").forEach(desc => {
      if (desc.id === id) {
        desc.classList.toggle("open");
      } else {
        desc.classList.remove("open");
      }
    });
  }
</script>


  <section id="testimonials">
    <h2>What Our Clients Say</h2>
    <div class="testimonial-container">
      <div class="testimonial-slider" id="testimonial-slider">
        <div class="testimonial">
          <p>"Raf helped me recover from my knee injury faster than I expected. The mobile service was so convenient!"</p>
          <h4>Sylwia L.</h4>
        </div>
        <div class="testimonial">
          <p>"I felt genuinely cared for throughout my rehab journey. A combination of rehab programme and manual therapy relieved me from chronic pain in upper back, shoulders and neck. Highly recommend Raf as a Physiotherapist."</p>
          <h4>David K.</h4>
        </div>
          <div class="testimonial">
          <p>"Professional and friendly. As an office worker I finally got rid of my migraines! The mobile visits fit perfectly into my busy schedule."</p>
          <h4>Linda S.</h4>
        </div>
        <div class="testimonial">
          <p>"The therapist is knowledgeable and kind. The massage sessions helped relieve my chronic back pain."</p>
          <h4>Tomek B.</h4>
        </div>
        <div class="testimonial">
          <p>"I appreciate the personalised rehab plans tailored to my sports injury. I’m back on the field stronger than ever."</p>
          <h4>Emily R.</h4>
        </div>
        <div class="testimonial">
          <p>"Excellent care and attention. The exercises Raf recommended really improved my mobility and pain levels."</p>
          <h4>James T.</h4>
        </div>
       </div>
    </div>
  </section>

 <!-- Footer -->
  <footer id="contact" style="background: #0d253f; color: white; text-align: center; padding: 1.5rem 2rem; font-family: 'Montserrat', sans-serif;">
    <p style="margin: 0.2rem 0; font-weight: 600; font-size: 1rem;">
      Opening Hours: <span style="font-weight: 400;">Mon–Fri: 5pm – 9pm | Sat: 9am – 5pm</span>
    </p>
    <p style="margin: 0.2rem 0; font-size: 1rem;">
      Contact us at 
      <a href="mailto:rehabjunctionyork@gmail.com" style="color: #ff9800; text-decoration: none;">rehabjunctionyork@gmail.com</a> 
      or call: <a href="tel:07477593373" style="color: #ff9800; text-decoration: none;">07477593373</a>
    </p>
    <p style="margin: 0.5rem 0 0 0; font-size: 0.9rem; color: #bbb;">
      &copy; 2025 Rehab Junction. All rights reserved.
    </p>
  </footer>

  <script>
    // Duplicate testimonials for seamless continuous scrolling
    window.addEventListener('DOMContentLoaded', () => {
      const slider = document.getElementById('testimonial-slider');
      const testimonials = Array.from(slider.children);
      testimonials.forEach(node => {
        const clone = node.cloneNode(true);
        slider.appendChild(clone);
      });
    });
  </script>

</body>
</html>
