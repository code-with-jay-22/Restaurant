<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0" />
    <title>Neshville Kenya — Fine Dining Experience</title>
    <link
      href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&family=Inter:wght@300;400;500;600&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&display=swap"
      rel="stylesheet" />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />
    <style>
      *,
      *::before,
      *::after {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }

      :root {
        --gold: #c9a96e;
        --gold-light: #e0c992;
        --gold-dark: #a88b4a;
        --white: #ffffff;
        --off-white: #f5f0eb;
        --cream: #faf8f5;
        --dark: #0a0a0a;
        --dark-2: #111111;
        --dark-3: #1a1a1a;
        --dark-4: #222222;
        --gray: #888888;
        --gray-light: #aaaaaa;
      }

      html {
        scroll-behavior: smooth;
        overflow-x: hidden;
      }

      body {
        font-family: 'Inter', sans-serif;
        background: var(--dark);
        color: var(--white);
        overflow-x: hidden;
      }

      ::selection {
        background: var(--gold);
        color: var(--dark);
      }

      ::-webkit-scrollbar {
        width: 8px;
      }

      ::-webkit-scrollbar-track {
        background: var(--dark);
      }

      ::-webkit-scrollbar-thumb {
        background: var(--gold);
        border-radius: 4px;
      }

      /* Loader */
      .loader {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: var(--dark);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 10000;
        transition:
          opacity 0.8s ease,
          visibility 0.8s ease;
      }

      .loader.hidden {
        opacity: 0;
        visibility: hidden;
      }

      .loader-text {
        font-family: 'Playfair Display', serif;
        font-size: 2.5rem;
        color: var(--gold);
        animation: pulse 1.5s ease-in-out infinite;
      }

      @keyframes pulse {
        0%,
        100% {
          opacity: 0.4;
          transform: scale(0.98);
        }
        50% {
          opacity: 1;
          transform: scale(1);
        }
      }

      /* Navbar */
      .navbar {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        padding: 20px 60px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        z-index: 1000;
        transition: all 0.4s ease;
      }

      .navbar.scrolled {
        background: rgba(10, 10, 10, 0.95);
        backdrop-filter: blur(20px);
        padding: 12px 60px;
        box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3);
      }

      .nav-logo {
        font-family: 'Playfair Display', serif;
        font-size: 1.6rem;
        font-weight: 700;
        color: var(--gold);
        text-decoration: none;
        letter-spacing: 2px;
      }

      .nav-logo span {
        font-weight: 300;
        color: var(--white);
        font-size: 0.8rem;
        display: block;
        letter-spacing: 4px;
        text-transform: uppercase;
      }

      .nav-links {
        display: flex;
        list-style: none;
        gap: 35px;
        align-items: center;
      }

      .nav-links a {
        color: var(--white);
        text-decoration: none;
        font-size: 0.85rem;
        font-weight: 400;
        letter-spacing: 1.5px;
        text-transform: uppercase;
        position: relative;
        transition: color 0.3s ease;
      }

      .nav-links a::after {
        content: '';
        position: absolute;
        bottom: -4px;
        left: 0;
        width: 0;
        height: 1px;
        background: var(--gold);
        transition: width 0.3s ease;
      }

      .nav-links a:hover {
        color: var(--gold);
      }

      .nav-links a:hover::after {
        width: 100%;
      }

      .nav-cta {
        padding: 10px 28px !important;
        border: 1px solid var(--gold) !important;
        color: var(--gold) !important;
        font-size: 0.8rem !important;
        letter-spacing: 2px !important;
        transition: all 0.3s ease !important;
      }

      .nav-cta:hover {
        background: var(--gold) !important;
        color: var(--dark) !important;
      }

      .menu-toggle {
        display: none;
        flex-direction: column;
        gap: 5px;
        cursor: pointer;
        z-index: 1001;
      }

      .menu-toggle span {
        width: 28px;
        height: 1.5px;
        background: var(--gold);
        transition: all 0.3s ease;
      }

      .menu-toggle.active span:nth-child(1) {
        transform: rotate(45deg) translate(4px, 4px);
      }

      .menu-toggle.active span:nth-child(2) {
        opacity: 0;
      }

      .menu-toggle.active span:nth-child(3) {
        transform: rotate(-45deg) translate(5px, -5px);
      }

      /* Hero Section */
      .hero {
        position: relative;
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        overflow: hidden;
      }

      .hero-bg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background:
          linear-gradient(
            135deg,
            rgba(10, 10, 10, 0.85) 0%,
            rgba(10, 10, 10, 0.4) 50%,
            rgba(10, 10, 10, 0.7) 100%
          ),
          url('https://images.unsplash.com/photo-1414235077428-338989a2e8c0?w=1920&q=80')
            center/cover no-repeat;
        animation: heroZoom 20s ease-in-out infinite alternate;
      }

      @keyframes heroZoom {
        0% {
          transform: scale(1);
        }
        100% {
          transform: scale(1.08);
        }
      }

      .hero-particles {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        overflow: hidden;
      }

      .particle {
        position: absolute;
        width: 2px;
        height: 2px;
        background: var(--gold);
        border-radius: 50%;
        opacity: 0;
        animation: floatUp linear infinite;
      }

      @keyframes floatUp {
        0% {
          opacity: 0;
          transform: translateY(100vh) scale(0);
        }
        10% {
          opacity: 0.6;
        }
        90% {
          opacity: 0.3;
        }
        100% {
          opacity: 0;
          transform: translateY(-10vh) scale(1);
        }
      }

      .hero-content {
        position: relative;
        z-index: 2;
        text-align: center;
        max-width: 900px;
        padding: 0 20px;
      }

      .hero-badge {
        display: inline-flex;
        align-items: center;
        gap: 10px;
        padding: 8px 24px;
        border: 1px solid rgba(201, 169, 110, 0.3);
        border-radius: 50px;
        margin-bottom: 30px;
        font-size: 0.75rem;
        letter-spacing: 3px;
        text-transform: uppercase;
        color: var(--gold);
        opacity: 0;
        animation: fadeInUp 1s ease 0.5s forwards;
      }

      .hero-badge::before,
      .hero-badge::after {
        content: '';
        width: 20px;
        height: 1px;
        background: var(--gold);
      }

      .hero h1 {
        font-family: 'Playfair Display', serif;
        font-size: clamp(2.5rem, 6vw, 5rem);
        font-weight: 700;
        line-height: 1.1;
        margin-bottom: 25px;
        opacity: 0;
        animation: fadeInUp 1s ease 0.7s forwards;
      }

      .hero h1 em {
        font-style: italic;
        color: var(--gold);
      }

      .hero p {
        font-size: 1.1rem;
        color: var(--gray-light);
        font-weight: 300;
        margin-bottom: 45px;
        letter-spacing: 1px;
        opacity: 0;
        animation: fadeInUp 1s ease 0.9s forwards;
      }

      .hero-buttons {
        display: flex;
        gap: 20px;
        justify-content: center;
        flex-wrap: wrap;
        opacity: 0;
        animation: fadeInUp 1s ease 1.1s forwards;
      }

      .btn-primary {
        padding: 16px 42px;
        background: var(--gold);
        color: var(--dark);
        border: none;
        font-size: 0.85rem;
        font-weight: 600;
        letter-spacing: 2px;
        text-transform: uppercase;
        cursor: pointer;
        text-decoration: none;
        transition: all 0.4s ease;
        position: relative;
        overflow: hidden;
      }

      .btn-primary::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(
          90deg,
          transparent,
          rgba(255, 255, 255, 0.2),
          transparent
        );
        transition: left 0.5s ease;
      }

      .btn-primary:hover::before {
        left: 100%;
      }

      .btn-primary:hover {
        background: var(--gold-light);
        transform: translateY(-2px);
        box-shadow: 0 10px 40px rgba(201, 169, 110, 0.3);
      }

      .btn-outline {
        padding: 16px 42px;
        background: transparent;
        color: var(--white);
        border: 1px solid rgba(255, 255, 255, 0.3);
        font-size: 0.85rem;
        font-weight: 400;
        letter-spacing: 2px;
        text-transform: uppercase;
        cursor: pointer;
        text-decoration: none;
        transition: all 0.4s ease;
      }

      .btn-outline:hover {
        border-color: var(--gold);
        color: var(--gold);
        transform: translateY(-2px);
      }

      .hero-scroll {
        position: absolute;
        bottom: 40px;
        left: 50%;
        transform: translateX(-50%);
        z-index: 2;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 8px;
        color: var(--gray);
        font-size: 0.7rem;
        letter-spacing: 3px;
        text-transform: uppercase;
        animation: bounce 2s ease-in-out infinite;
      }

      .hero-scroll .scroll-line {
        width: 1px;
        height: 40px;
        background: linear-gradient(to bottom, var(--gold), transparent);
      }

      @keyframes bounce {
        0%,
        100% {
          transform: translateX(-50%) translateY(0);
        }
        50% {
          transform: translateX(-50%) translateY(10px);
        }
      }

      @keyframes fadeInUp {
        from {
          opacity: 0;
          transform: translateY(30px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      /* Section Styles */
      .section {
        padding: 120px 60px;
      }

      .section-header {
        text-align: center;
        margin-bottom: 70px;
      }

      .section-label {
        font-size: 0.75rem;
        letter-spacing: 4px;
        text-transform: uppercase;
        color: var(--gold);
        margin-bottom: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 15px;
      }

      .section-label::before,
      .section-label::after {
        content: '';
        width: 30px;
        height: 1px;
        background: var(--gold);
      }

      .section-title {
        font-family: 'Playfair Display', serif;
        font-size: clamp(2rem, 4vw, 3.2rem);
        font-weight: 600;
        margin-bottom: 20px;
      }

      .section-subtitle {
        font-size: 1rem;
        color: var(--gray);
        font-weight: 300;
        max-width: 600px;
        margin: 0 auto;
        line-height: 1.7;
      }

      .gold-line {
        width: 60px;
        height: 2px;
        background: var(--gold);
        margin: 20px auto 0;
      }

      /* About Section */
      .about {
        background: var(--dark-2);
      }

      .about-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 80px;
        align-items: center;
        max-width: 1200px;
        margin: 0 auto;
      }

      .about-image {
        position: relative;
      }

      .about-image img {
        width: 100%;
        height: 550px;
        object-fit: cover;
        filter: brightness(0.9);
      }

      .about-image::before {
        content: '';
        position: absolute;
        top: 20px;
        left: 20px;
        width: 100%;
        height: 100%;
        border: 1px solid var(--gold);
        z-index: -1;
      }

      .about-exp {
        position: absolute;
        bottom: -30px;
        right: -30px;
        background: var(--gold);
        color: var(--dark);
        padding: 25px 30px;
        text-align: center;
      }

      .about-exp .number {
        font-family: 'Playfair Display', serif;
        font-size: 3rem;
        font-weight: 700;
        line-height: 1;
      }

      .about-exp .text {
        font-size: 0.75rem;
        letter-spacing: 2px;
        text-transform: uppercase;
        font-weight: 600;
      }

      .about-content .section-label {
        justify-content: flex-start;
      }

      .about-content .section-label::before {
        display: none;
      }

      .about-content h2 {
        font-family: 'Playfair Display', serif;
        font-size: 2.5rem;
        margin-bottom: 25px;
        line-height: 1.2;
      }

      .about-content h2 em {
        font-style: italic;
        color: var(--gold);
      }

      .about-content p {
        color: var(--gray-light);
        line-height: 1.8;
        margin-bottom: 20px;
        font-size: 0.95rem;
      }

      .about-features {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 25px;
        margin-top: 35px;
      }

      .about-feature {
        display: flex;
        align-items: flex-start;
        gap: 12px;
      }

      .about-feature i {
        color: var(--gold);
        font-size: 1.2rem;
        margin-top: 3px;
      }

      .about-feature h4 {
        font-size: 0.9rem;
        font-weight: 600;
        margin-bottom: 4px;
      }

      .about-feature p {
        font-size: 0.8rem !important;
        color: var(--gray) !important;
        margin-bottom: 0 !important;
      }

      /* Menu Section */
      .menu {
        background: var(--dark);
      }

      .menu-tabs {
        display: flex;
        justify-content: center;
        gap: 10px;
        margin-bottom: 50px;
        flex-wrap: wrap;
      }

      .menu-tab {
        padding: 10px 30px;
        border: 1px solid rgba(201, 169, 110, 0.2);
        background: transparent;
        color: var(--gray);
        font-size: 0.8rem;
        letter-spacing: 2px;
        text-transform: uppercase;
        cursor: pointer;
        transition: all 0.3s ease;
        font-family: 'Inter', sans-serif;
      }

      .menu-tab:hover,
      .menu-tab.active {
        background: var(--gold);
        color: var(--dark);
        border-color: var(--gold);
      }

      .menu-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 30px;
        max-width: 1200px;
        margin: 0 auto;
      }

      .menu-card {
        background: var(--dark-3);
        border: 1px solid rgba(255, 255, 255, 0.05);
        overflow: hidden;
        transition: all 0.4s ease;
        opacity: 0;
        transform: translateY(30px);
      }

      .menu-card.visible {
        opacity: 1;
        transform: translateY(0);
      }

      .menu-card:hover {
        transform: translateY(-8px);
        border-color: rgba(201, 169, 110, 0.2);
        box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
      }

      .menu-card-img {
        height: 220px;
        overflow: hidden;
        position: relative;
      }

      .menu-card-img img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.6s ease;
      }

      .menu-card:hover .menu-card-img img {
        transform: scale(1.1);
      }

      .menu-card-badge {
        position: absolute;
        top: 15px;
        right: 15px;
        background: var(--gold);
        color: var(--dark);
        padding: 4px 12px;
        font-size: 0.65rem;
        font-weight: 600;
        letter-spacing: 1px;
        text-transform: uppercase;
      }

      .menu-card-body {
        padding: 25px;
      }

      .menu-card-top {
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        margin-bottom: 8px;
      }

      .menu-card h3 {
        font-family: 'Playfair Display', serif;
        font-size: 1.2rem;
        font-weight: 600;
      }

      .menu-card-price {
        font-family: 'Playfair Display', serif;
        font-size: 1.3rem;
        color: var(--gold);
        font-weight: 600;
        white-space: nowrap;
      }

      .menu-card p {
        color: var(--gray);
        font-size: 0.85rem;
        line-height: 1.6;
      }

      .menu-card-bottom {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 15px;
        padding-top: 15px;
        border-top: 1px solid rgba(255, 255, 255, 0.05);
      }

      .menu-card-rating {
        color: var(--gold);
        font-size: 0.8rem;
      }

      .menu-card-add {
        width: 36px;
        height: 36px;
        border: 1px solid rgba(201, 169, 110, 0.3);
        background: transparent;
        color: var(--gold);
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all 0.3s ease;
      }

      .menu-card-add:hover {
        background: var(--gold);
        color: var(--dark);
      }

      /* Gallery Section */
      .gallery {
        background: var(--dark-2);
      }

      .gallery-grid {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        grid-template-rows: repeat(2, 250px);
        gap: 15px;
        max-width: 1200px;
        margin: 0 auto;
      }

      .gallery-item {
        overflow: hidden;
        position: relative;
        cursor: pointer;
      }

      .gallery-item:nth-child(1) {
        grid-column: span 2;
        grid-row: span 2;
      }

      .gallery-item img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.6s ease;
      }

      .gallery-item::after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(
          to bottom,
          transparent 50%,
          rgba(10, 10, 10, 0.7)
        );
        opacity: 0;
        transition: opacity 0.4s ease;
      }

      .gallery-item:hover img {
        transform: scale(1.15);
      }

      .gallery-item:hover::after {
        opacity: 1;
      }

      .gallery-overlay {
        position: absolute;
        bottom: 20px;
        left: 20px;
        z-index: 2;
        opacity: 0;
        transform: translateY(10px);
        transition: all 0.4s ease;
      }

      .gallery-item:hover .gallery-overlay {
        opacity: 1;
        transform: translateY(0);
      }

      .gallery-overlay h4 {
        font-family: 'Playfair Display', serif;
        font-size: 1.1rem;
        margin-bottom: 4px;
      }

      .gallery-overlay p {
        font-size: 0.75rem;
        color: var(--gold);
        letter-spacing: 2px;
        text-transform: uppercase;
      }

      .gallery-zoom {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%) scale(0);
        z-index: 2;
        width: 50px;
        height: 50px;
        border: 1px solid var(--gold);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--gold);
        transition: all 0.4s ease;
      }

      .gallery-item:hover .gallery-zoom {
        transform: translate(-50%, -50%) scale(1);
      }

      /* Testimonials */
      .testimonials {
        background: var(--dark);
        position: relative;
      }

      .testimonials::before {
        content: '"';
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        font-family: 'Playfair Display', serif;
        font-size: 30rem;
        color: rgba(201, 169, 110, 0.03);
        line-height: 1;
        pointer-events: none;
      }

      .testimonials-slider {
        max-width: 900px;
        margin: 0 auto;
        position: relative;
        overflow: hidden;
      }

      .testimonials-track {
        display: flex;
        transition: transform 0.6s ease;
      }

      .testimonial-card {
        min-width: 100%;
        padding: 0 40px;
        text-align: center;
      }

      .testimonial-stars {
        color: var(--gold);
        font-size: 1rem;
        margin-bottom: 25px;
        display: flex;
        justify-content: center;
        gap: 4px;
      }

      .testimonial-text {
        font-family: 'Cormorant Garamond', serif;
        font-size: 1.5rem;
        font-style: italic;
        line-height: 1.8;
        color: var(--off-white);
        margin-bottom: 35px;
        font-weight: 300;
      }

      .testimonial-author {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
      }

      .testimonial-author img {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        object-fit: cover;
        border: 2px solid var(--gold);
      }

      .testimonial-author h4 {
        font-size: 1rem;
        font-weight: 600;
      }

      .testimonial-author p {
        font-size: 0.8rem;
        color: var(--gray);
      }

      .testimonial-dots {
        display: flex;
        justify-content: center;
        gap: 10px;
        margin-top: 40px;
      }

      .testimonial-dot {
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.2);
        cursor: pointer;
        transition: all 0.3s ease;
      }

      .testimonial-dot.active {
        background: var(--gold);
        width: 25px;
        border-radius: 4px;
      }

      /* Booking Section */
      .booking {
        background: var(--dark-2);
        position: relative;
      }

      .booking::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(
          135deg,
          rgba(201, 169, 110, 0.03) 0%,
          transparent 50%
        );
        pointer-events: none;
      }

      .booking-container {
        max-width: 1000px;
        margin: 0 auto;
        position: relative;
      }

      .booking-form {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 25px;
      }

      .form-group {
        display: flex;
        flex-direction: column;
        gap: 8px;
      }

      .form-group.full {
        grid-column: span 2;
      }

      .form-group label {
        font-size: 0.75rem;
        letter-spacing: 2px;
        text-transform: uppercase;
        color: var(--gold);
      }

      .form-group input,
      .form-group select,
      .form-group textarea {
        padding: 16px 20px;
        background: rgba(255, 255, 255, 0.03);
        border: 1px solid rgba(255, 255, 255, 0.1);
        color: var(--white);
        font-family: 'Inter', sans-serif;
        font-size: 0.95rem;
        transition: all 0.3s ease;
        outline: none;
        -webkit-appearance: none;
      }

      .form-group input:focus,
      .form-group select:focus,
      .form-group textarea:focus {
        border-color: var(--gold);
        background: rgba(201, 169, 110, 0.03);
      }

      .form-group input::placeholder,
      .form-group textarea::placeholder {
        color: var(--gray);
      }

      .form-group select option {
        background: var(--dark-3);
      }

      .form-group textarea {
        resize: vertical;
        min-height: 120px;
      }

      .booking-form .btn-primary {
        grid-column: span 2;
        width: fit-content;
        margin: 10px auto 0;
        padding: 18px 60px;
      }

      /* Contact Section */
      .contact {
        background: var(--dark);
      }

      .contact-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 60px;
        max-width: 1200px;
        margin: 0 auto;
      }

      .contact-info {
        display: flex;
        flex-direction: column;
        gap: 30px;
      }

      .contact-card {
        display: flex;
        gap: 20px;
        padding: 25px;
        background: var(--dark-3);
        border: 1px solid rgba(255, 255, 255, 0.05);
        transition: all 0.3s ease;
      }

      .contact-card:hover {
        border-color: rgba(201, 169, 110, 0.2);
        transform: translateX(5px);
      }

      .contact-icon {
        width: 50px;
        height: 50px;
        border: 1px solid var(--gold);
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--gold);
        font-size: 1.1rem;
        flex-shrink: 0;
      }

      .contact-card h4 {
        font-size: 1rem;
        font-weight: 600;
        margin-bottom: 6px;
      }

      .contact-card p {
        font-size: 0.9rem;
        color: var(--gray-light);
        line-height: 1.6;
      }

      .contact-map {
        border: 1px solid rgba(255, 255, 255, 0.05);
        overflow: hidden;
      }

      .contact-map iframe {
        width: 100%;
        height: 100%;
        filter: grayscale(1) invert(0) contrast(0.9) brightness(0.8);
      }

      /* Footer */
      .footer {
        background: var(--dark-2);
        padding: 80px 60px 30px;
        border-top: 1px solid rgba(255, 255, 255, 0.05);
      }

      .footer-top {
        display: grid;
        grid-template-columns: 2fr 1fr 1fr 1.5fr;
        gap: 50px;
        max-width: 1200px;
        margin: 0 auto 60px;
      }

      .footer-brand h3 {
        font-family: 'Playfair Display', serif;
        font-size: 1.8rem;
        color: var(--gold);
        margin-bottom: 5px;
      }

      .footer-brand h3 span {
        color: var(--white);
        font-weight: 300;
      }

      .footer-brand p {
        color: var(--gray);
        font-size: 0.9rem;
        line-height: 1.7;
        margin-bottom: 20px;
      }

      .footer-social {
        display: flex;
        gap: 12px;
      }

      .footer-social a {
        width: 42px;
        height: 42px;
        border: 1px solid rgba(255, 255, 255, 0.1);
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--white);
        text-decoration: none;
        transition: all 0.3s ease;
      }

      .footer-social a:hover {
        border-color: var(--gold);
        color: var(--gold);
        transform: translateY(-3px);
      }

      .footer-col h4 {
        font-size: 0.85rem;
        font-weight: 600;
        letter-spacing: 2px;
        text-transform: uppercase;
        margin-bottom: 25px;
        color: var(--gold);
      }

      .footer-col ul {
        list-style: none;
        display: flex;
        flex-direction: column;
        gap: 12px;
      }

      .footer-col ul a {
        color: var(--gray);
        text-decoration: none;
        font-size: 0.9rem;
        transition: color 0.3s ease;
      }

      .footer-col ul a:hover {
        color: var(--gold);
      }

      .footer-hours li {
        display: flex;
        justify-content: space-between;
        color: var(--gray);
        font-size: 0.85rem;
        padding: 8px 0;
        border-bottom: 1px solid rgba(255, 255, 255, 0.03);
      }

      .footer-hours li span:last-child {
        color: var(--off-white);
      }

      .footer-bottom {
        border-top: 1px solid rgba(255, 255, 255, 0.05);
        padding-top: 25px;
        max-width: 1200px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .footer-bottom p {
        color: var(--gray);
        font-size: 0.8rem;
      }

      .footer-bottom a {
        color: var(--gold);
        text-decoration: none;
      }

      /* Scroll Animations */
      .reveal {
        opacity: 0;
        transform: translateY(40px);
        transition: all 0.8s ease;
      }

      .reveal.visible {
        opacity: 1;
        transform: translateY(0);
      }

      .reveal-left {
        opacity: 0;
        transform: translateX(-40px);
        transition: all 0.8s ease;
      }

      .reveal-left.visible {
        opacity: 1;
        transform: translateX(0);
      }

      .reveal-right {
        opacity: 0;
        transform: translateX(40px);
        transition: all 0.8s ease;
      }

      .reveal-right.visible {
        opacity: 1;
        transform: translateX(0);
      }

      /* Back to top */
      .back-to-top {
        position: fixed;
        bottom: 30px;
        right: 30px;
        width: 48px;
        height: 48px;
        background: var(--gold);
        color: var(--dark);
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease;
        z-index: 999;
        border: none;
        font-size: 1.1rem;
      }

      .back-to-top.show {
        opacity: 1;
        visibility: visible;
      }

      .back-to-top:hover {
        transform: translateY(-3px);
        box-shadow: 0 10px 30px rgba(201, 169, 110, 0.3);
      }

      /* Lightbox */
      .lightbox {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.95);
        z-index: 10000;
        display: flex;
        align-items: center;
        justify-content: center;
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease;
      }

      .lightbox.active {
        opacity: 1;
        visibility: visible;
      }

      .lightbox img {
        max-width: 85%;
        max-height: 85vh;
        object-fit: contain;
      }

      .lightbox-close {
        position: absolute;
        top: 30px;
        right: 30px;
        width: 50px;
        height: 50px;
        border: 1px solid var(--gold);
        background: transparent;
        color: var(--gold);
        font-size: 1.3rem;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all 0.3s ease;
      }

      .lightbox-close:hover {
        background: var(--gold);
        color: var(--dark);
      }

      /* Mobile Responsive */
      @media (max-width: 1024px) {
        .section {
          padding: 80px 30px;
        }

        .navbar {
          padding: 15px 30px;
        }

        .navbar.scrolled {
          padding: 10px 30px;
        }

        .about-grid {
          gap: 40px;
        }

        .gallery-grid {
          grid-template-columns: repeat(2, 1fr);
          grid-template-rows: auto;
        }

        .gallery-item:nth-child(1) {
          grid-column: span 2;
          grid-row: span 1;
        }

        .gallery-item {
          height: 220px;
        }

        .footer-top {
          grid-template-columns: 1fr 1fr;
        }
      }

      @media (max-width: 768px) {
        .nav-links {
          position: fixed;
          top: 0;
          right: -100%;
          width: 80%;
          max-width: 350px;
          height: 100vh;
          background: var(--dark-2);
          flex-direction: column;
          justify-content: center;
          align-items: center;
          transition: right 0.4s ease;
          border-left: 1px solid rgba(201, 169, 110, 0.1);
        }

        .nav-links.open {
          right: 0;
        }

        .nav-links a {
          font-size: 1rem;
        }

        .menu-toggle {
          display: flex;
        }

        .hero h1 {
          font-size: 2.2rem;
        }

        .hero p {
          font-size: 0.95rem;
        }

        .hero-buttons {
          flex-direction: column;
          align-items: center;
        }

        .btn-primary,
        .btn-outline {
          width: 220px;
          text-align: center;
        }

        .about-grid {
          grid-template-columns: 1fr;
        }

        .about-image::before {
          top: 10px;
          left: 10px;
        }

        .about-exp {
          right: 10px;
          bottom: -20px;
        }

        .about-image img {
          height: 400px;
        }

        .about-features {
          grid-template-columns: 1fr;
        }

        .menu-grid {
          grid-template-columns: 1fr;
        }

        .gallery-grid {
          grid-template-columns: 1fr 1fr;
          gap: 8px;
        }

        .gallery-item:nth-child(1) {
          grid-column: span 2;
        }

        .booking-form {
          grid-template-columns: 1fr;
        }

        .form-group.full,
        .booking-form .btn-primary {
          grid-column: span 1;
        }

        .contact-grid {
          grid-template-columns: 1fr;
        }

        .footer-top {
          grid-template-columns: 1fr;
          gap: 30px;
        }

        .footer-bottom {
          flex-direction: column;
          gap: 10px;
          text-align: center;
        }

        .section {
          padding: 70px 20px;
        }

        .testimonial-text {
          font-size: 1.2rem;
        }
      }

      @media (max-width: 480px) {
        .hero h1 {
          font-size: 1.8rem;
        }

        .gallery-grid {
          grid-template-columns: 1fr;
        }

        .gallery-item:nth-child(1) {
          grid-column: span 1;
        }

        .gallery-item {
          height: 200px;
        }

        .hero-badge {
          font-size: 0.65rem;
        }
      }
    </style>
  </head>
  <body>
    <!-- Loader -->
    <div
      class="loader"
      id="loader">
      <div class="loader-text">Neshville</div>
    </div>

    <!-- Navbar -->
    <nav
      class="navbar"
      id="navbar">
      <a
        href="#"
        class="nav-logo">
        Neshville
        <span>Kenya</span>
      </a>
      <ul
        class="nav-links"
        id="navLinks">
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#menu">Menu</a></li>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#testimonials">Reviews</a></li>
        <li><a href="#booking">Book</a></li>
        <li><a href="#contact">Contact</a></li>
        <li>
          <a
            href="#booking"
            class="nav-cta"
            >Reserve</a
          >
        </li>
      </ul>
      <div
        class="menu-toggle"
        id="menuToggle">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </nav>

    <!-- Hero Section -->
    <section
      class="hero"
      id="home">
      <div class="hero-bg"></div>
      <div
        class="hero-particles"
        id="particles"></div>
      <div class="hero-content">
        <div class="hero-badge">Since 2018 — Nairobi, Kenya</div>
        <h1>Experience Fine Dining<br />Like <em>Never Before</em></h1>
        <p>
          Premium cuisine in the heart of Kenya — where every dish tells a story
        </p>
        <div class="hero-buttons">
          <a
            href="#booking"
            class="btn-primary"
            >Book a Table</a
          >
          <a
            href="#menu"
            class="btn-outline"
            >Explore Menu</a
          >
        </div>
      </div>
      <div class="hero-scroll">
        <span>Scroll</span>
        <div class="scroll-line"></div>
      </div>
    </section>

    <!-- About Section -->
    <section
      class="about section"
      id="about">
      <div class="about-grid">
        <div class="about-image reveal-left">
          <img
            src="https://images.unsplash.com/photo-1600891964092-4316c288032e?w=800&q=80"
            alt="Restaurant Interior" />
          <div class="about-exp">
            <div class="number">7+</div>
            <div class="text">Years of Excellence</div>
          </div>
        </div>
        <div class="about-content reveal-right">
          <div class="section-label">Our Story</div>
          <h2>Crafted with <em>Passion</em>, Served with <em>Elegance</em></h2>
          <p>
            Neshville Kenya was born from a passion to redefine fine dining in
            East Africa. Nestled in the vibrant heart of Nairobi, we bring
            together the finest locally sourced ingredients with world-class
            culinary techniques.
          </p>
          <p>
            Our master chefs, trained in Michelin-starred kitchens across Europe
            and Asia, create dishes that celebrate Kenya's rich agricultural
            heritage while embracing global flavors.
          </p>
          <div class="about-features">
            <div class="about-feature">
              <i class="fas fa-utensils"></i>
              <div>
                <h4>Master Chefs</h4>
                <p>Trained at top culinary schools worldwide</p>
              </div>
            </div>
            <div class="about-feature">
              <i class="fas fa-leaf"></i>
              <div>
                <h4>Fresh Ingredients</h4>
                <p>Locally sourced, organic produce daily</p>
              </div>
            </div>
            <div class="about-feature">
              <i class="fas fa-glass-cheers"></i>
              <div>
                <h4>Fine Wines</h4>
                <p>500+ premium wine selections</p>
              </div>
            </div>
            <div class="about-feature">
              <i class="fas fa-concierge-bell"></i>
              <div>
                <h4>White Glove Service</h4>
                <p>Dedicated concierge for every guest</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Menu Section -->
    <section
      class="menu section"
      id="menu">
      <div class="section-header reveal">
        <div class="section-label">Our Menu</div>
        <h2 class="section-title">
          Curated Culinary
          <em
            style="
              font-family: 'Playfair Display';
              font-style: italic;
              color: var(--gold);
            "
            >Masterpieces</em
          >
        </h2>
        <p class="section-subtitle">
          Each dish is a work of art, prepared with precision and passion by our
          award-winning culinary team
        </p>
      </div>

      <div class="menu-tabs reveal">
        <button
          class="menu-tab active"
          data-category="all">
          All
        </button>
        <button
          class="menu-tab"
          data-category="starters">
          Starters
        </button>
        <button
          class="menu-tab"
          data-category="mains">
          Main Course
        </button>
        <button
          class="menu-tab"
          data-category="desserts">
          Desserts
        </button>
        <button
          class="menu-tab"
          data-category="drinks">
          Drinks
        </button>
      </div>

      <div
        class="menu-grid"
        id="menuGrid">
        <!-- Cards will be injected by JS -->
      </div>
    </section>

    <!-- Gallery Section -->
    <section
      class="gallery section"
      id="gallery">
      <div class="section-header reveal">
        <div class="section-label">Gallery</div>
        <h2 class="section-title">
          A Glimpse of
          <em
            style="
              font-family: 'Playfair Display';
              font-style: italic;
              color: var(--gold);
            "
            >Elegance</em
          >
        </h2>
        <p class="section-subtitle">
          Immerse yourself in the refined atmosphere of Neshville Kenya
        </p>
      </div>
      <div class="gallery-grid reveal">
        <div
          class="gallery-item"
          data-src="https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?w=1200&q=80">
          <img
            src="https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?w=800&q=80"
            alt="Restaurant Interior" />
          <div class="gallery-zoom"><i class="fas fa-expand"></i></div>
          <div class="gallery-overlay">
            <h4>Main Dining Hall</h4>
            <p>Elegant Ambiance</p>
          </div>
        </div>
        <div
          class="gallery-item"
          data-src="https://images.unsplash.com/photo-1546833998-877b37c2e5c6?w=1200&q=80">
          <img
            src="https://images.unsplash.com/photo-1546833998-877b37c2e5c6?w=600&q=80"
            alt="Chef" />
          <div class="gallery-zoom"><i class="fas fa-expand"></i></div>
          <div class="gallery-overlay">
            <h4>Our Kitchen</h4>
            <p>Where Magic Happens</p>
          </div>
        </div>
        <div
          class="gallery-item"
          data-src="https://images.unsplash.com/photo-1551218808-94e220e084d2?w=1200&q=80">
          <img
            src="https://images.unsplash.com/photo-1551218808-94e220e084d2?w=600&q=80"
            alt="Plated Dish" />
          <div class="gallery-zoom"><i class="fas fa-expand"></i></div>
          <div class="gallery-overlay">
            <h4>Culinary Art</h4>
            <p>Signature Dishes</p>
          </div>
        </div>
        <div
          class="gallery-item"
          data-src="https://images.unsplash.com/photo-1470337458703-46ad1756a187?w=1200&q=80">
          <img
            src="https://images.unsplash.com/photo-1470337458703-46ad1756a187?w=600&q=80"
            alt="Cocktails" />
          <div class="gallery-zoom"><i class="fas fa-expand"></i></div>
          <div class="gallery-overlay">
            <h4>Premium Bar</h4>
            <p>Craft Cocktails</p>
          </div>
        </div>
        <div
          class="gallery-item"
          data-src="https://images.unsplash.com/photo-1550966871-3ed3cdb51f3a?w=1200&q=80">
          <img
            src="https://images.unsplash.com/photo-1550966871-3ed3cdb51f3a?w=600&q=80"
            alt="Private Dining" />
          <div class="gallery-zoom"><i class="fas fa-expand"></i></div>
          <div class="gallery-overlay">
            <h4>Private Dining</h4>
            <p>Intimate Experience</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Lightbox -->
    <div
      class="lightbox"
      id="lightbox">
      <button
        class="lightbox-close"
        id="lightboxClose">
        <i class="fas fa-times"></i>
      </button>
      <img
        src=""
        alt=""
        id="lightboxImg" />
    </div>

    <!-- Testimonials -->
    <section
      class="testimonials section"
      id="testimonials">
      <div class="section-header reveal">
        <div class="section-label">Testimonials</div>
        <h2 class="section-title">
          What Our
          <em
            style="
              font-family: 'Playfair Display';
              font-style: italic;
              color: var(--gold);
            "
            >Guests</em
          >
          Say
        </h2>
        <p class="section-subtitle">
          Trusted by thousands of discerning diners across Kenya
        </p>
      </div>
      <div class="testimonials-slider reveal">
        <div
          class="testimonials-track"
          id="testimonialsTrack">
          <div class="testimonial-card">
            <div class="testimonial-stars">
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
            </div>
            <p class="testimonial-text">
              "An absolutely extraordinary dining experience. The attention to
              detail in every dish, the impeccable service, and the ambiance
              made our anniversary celebration truly unforgettable. Neshville is
              in a league of its own."
            </p>
            <div class="testimonial-author">
              <img
                src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=100&q=80"
                alt="Amina Wanjiku" />
              <h4>Amina Wanjiku</h4>
              <p>Entrepreneur, Nairobi</p>
            </div>
          </div>
          <div class="testimonial-card">
            <div class="testimonial-stars">
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
            </div>
            <p class="testimonial-text">
              "I've dined at Michelin-starred restaurants across Europe, and
              Neshville matches that standard effortlessly. The fusion of local
              Kenyan flavors with international techniques is nothing short of
              genius."
            </p>
            <div class="testimonial-author">
              <img
                src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=100&q=80"
                alt="James Mwangi" />
              <h4>James Mwangi</h4>
              <p>Food Critic, Travel Magazine</p>
            </div>
          </div>
          <div class="testimonial-card">
            <div class="testimonial-stars">
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star"></i>
              <i class="fas fa-star-half-alt"></i>
            </div>
            <p class="testimonial-text">
              "The private dining room was perfect for our corporate event. The
              team at Neshville went above and beyond to accommodate every
              request. The tasting menu was phenomenal — every course was a
              masterpiece."
            </p>
            <div class="testimonial-author">
              <img
                src="https://images.unsplash.com/photo-1438761681033-6461ffad8d80?w=100&q=80"
                alt="Sarah Ochieng" />
              <h4>Sarah Ochieng</h4>
              <p>CEO, Meridian Group</p>
            </div>
          </div>
        </div>
        <div
          class="testimonial-dots"
          id="testimonialDots">
          <div
            class="testimonial-dot active"
            data-index="0"></div>
          <div
            class="testimonial-dot"
            data-index="1"></div>
          <div
            class="testimonial-dot"
            data-index="2"></div>
        </div>
      </div>
    </section>

    <!-- Booking Section -->
    <section
      class="booking section"
      id="booking">
      <div class="section-header reveal">
        <div class="section-label">Reservations</div>
        <h2 class="section-title">
          Book Your
          <em
            style="
              font-family: 'Playfair Display';
              font-style: italic;
              color: var(--gold);
            "
            >Table</em
          >
        </h2>
        <p class="section-subtitle">
          Reserve your spot for an unforgettable dining experience
        </p>
      </div>
      <div class="booking-container reveal">
        <form
          class="booking-form"
          id="bookingForm">
          <div class="form-group">
            <label>Full Name</label>
            <input
              type="text"
              placeholder="Enter your name"
              required />
          </div>
          <div class="form-group">
            <label>Email Address</label>
            <input
              type="email"
              placeholder="Enter your email"
              required />
          </div>
          <div class="form-group">
            <label>Phone Number</label>
            <input
              type="tel"
              placeholder="+254 700 000 000" />
          </div>
          <div class="form-group">
            <label>Number of Guests</label>
            <select required>
              <option value="">Select guests</option>
              <option value="1">1 Guest</option>
              <option value="2">2 Guests</option>
              <option value="3">3 Guests</option>
              <option value="4">4 Guests</option>
              <option value="5">5 Guests</option>
              <option value="6">6 Guests</option>
              <option value="7-10">7-10 Guests</option>
              <option value="10+">10+ Guests</option>
            </select>
          </div>
          <div class="form-group">
            <label>Date</label>
            <input
              type="date"
              required />
          </div>
          <div class="form-group">
            <label>Preferred Time</label>
            <select required>
              <option value="">Select time</option>
              <option>12:00 PM</option>
              <option>12:30 PM</option>
              <option>1:00 PM</option>
              <option>1:30 PM</option>
              <option>2:00 PM</option>
              <option>6:00 PM</option>
              <option>6:30 PM</option>
              <option>7:00 PM</option>
              <option>7:30 PM</option>
              <option>8:00 PM</option>
              <option>8:30 PM</option>
              <option>9:00 PM</option>
              <option>9:30 PM</option>
            </select>
          </div>
          <div class="form-group full">
            <label>Special Requests</label>
            <textarea
              placeholder="Allergies, special occasions, dietary requirements..."></textarea>
          </div>
          <button
            type="submit"
            class="btn-primary">
            Confirm Reservation
          </button>
        </form>
      </div>
    </section>

    <!-- Contact Section -->
    <section
      class="contact section"
      id="contact">
      <div class="section-header reveal">
        <div class="section-label">Get in Touch</div>
        <h2 class="section-title">
          Contact
          <em
            style="
              font-family: 'Playfair Display';
              font-style: italic;
              color: var(--gold);
            "
            >Us</em
          >
        </h2>
        <p class="section-subtitle">
          We'd love to hear from you. Visit us or reach out directly.
        </p>
      </div>
      <div class="contact-grid">
        <div class="contact-info reveal-left">
          <div class="contact-card">
            <div class="contact-icon">
              <i class="fas fa-map-marker-alt"></i>
            </div>
            <div>
              <h4>Our Location</h4>
              <p>
                Westlands Business Park, 4th Floor<br />Waiyaki Way, Nairobi,
                Kenya
              </p>
            </div>
          </div>
          <div class="contact-card">
            <div class="contact-icon"><i class="fas fa-phone-alt"></i></div>
            <div>
              <h4>Call Us</h4>
              <p>+254 712 345 678<br />+254 720 000 111</p>
            </div>
          </div>
          <div class="contact-card">
            <div class="contact-icon"><i class="fas fa-envelope"></i></div>
            <div>
              <h4>Email Us</h4>
              <p>reservations@neshville.co.ke<br />events@neshville.co.ke</p>
            </div>
          </div>
          <div class="contact-card">
            <div class="contact-icon"><i class="fas fa-clock"></i></div>
            <div>
              <h4>Opening Hours</h4>
              <p>
                Mon–Thu: 12:00 PM – 11:00 PM<br />Fri–Sun: 12:00 PM – 12:00 AM
              </p>
            </div>
          </div>
        </div>
        <div class="contact-map reveal-right">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3988.8461!2d36.8022!3d-1.2695!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMcKwMTYnMDkuOCJTIDM2wrA0OCcyMy45IkU!5e0!3m2!1sen!2ske!4v1234567890"
            height="450"
            style="border: 0; width: 100%"
            allowfullscreen=""
            loading="lazy"></iframe>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-top">
        <div class="footer-brand">
          <h3>Neshville <span>Kenya</span></h3>
          <p>
            A premium fine dining destination where Kenyan flavors meet
            world-class culinary artistry. Every meal is a celebration.
          </p>
          <div class="footer-social">
            <a href="#"><i class="fab fa-instagram"></i></a>
            <a href="#"><i class="fab fa-facebook-f"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
            <a href="#"><i class="fab fa-tripadvisor"></i></a>
          </div>
        </div>
        <div class="footer-col">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About Us</a></li>
            <li><a href="#menu">Our Menu</a></li>
            <li><a href="#gallery">Gallery</a></li>
            <li><a href="#booking">Reservations</a></li>
          </ul>
        </div>
        <div class="footer-col">
          <h4>Experiences</h4>
          <ul>
            <li><a href="#">Private Dining</a></li>
            <li><a href="#">Wine Pairing</a></li>
            <li><a href="#">Chef's Table</a></li>
            <li><a href="#">Cocktail Bar</a></li>
            <li><a href="#">Events & Catering</a></li>
          </ul>
        </div>
        <div class="footer-col">
          <h4>Opening Hours</h4>
          <ul class="footer-hours">
            <li><span>Monday</span><span>12PM – 11PM</span></li>
            <li><span>Tuesday</span><span>12PM – 11PM</span></li>
            <li><span>Wednesday</span><span>12PM – 11PM</span></li>
            <li><span>Thursday</span><span>12PM – 11PM</span></li>
            <li><span>Friday</span><span>12PM – 12AM</span></li>
            <li><span>Saturday</span><span>12PM – 12AM</span></li>
            <li><span>Sunday</span><span>12PM – 10PM</span></li>
          </ul>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2025 <a href="#">Neshville Kenya</a>. All rights reserved.</p>
        <p>
          Crafted with
          <i
            class="fas fa-heart"
            style="color: var(--gold); font-size: 0.7rem"></i>
          in Nairobi
        </p>
      </div>
    </footer>

    <!-- Back to Top -->
    <button
      class="back-to-top"
      id="backToTop">
      <i class="fas fa-arrow-up"></i>
    </button>

    <script>
      // Loader
      window.addEventListener('load', () => {
        setTimeout(() => {
          document.getElementById('loader').classList.add('hidden');
        }, 1500);
      });

      // Navbar scroll
      const navbar = document.getElementById('navbar');
      window.addEventListener('scroll', () => {
        if (window.scrollY > 50) {
          navbar.classList.add('scrolled');
        } else {
          navbar.classList.remove('scrolled');
        }
      });

      // Mobile menu
      const menuToggle = document.getElementById('menuToggle');
      const navLinks = document.getElementById('navLinks');

      menuToggle.addEventListener('click', () => {
        menuToggle.classList.toggle('active');
        navLinks.classList.toggle('open');
      });

      navLinks.querySelectorAll('a').forEach((link) => {
        link.addEventListener('click', () => {
          menuToggle.classList.remove('active');
          navLinks.classList.remove('open');
        });
      });

      // Particles
      const particlesContainer = document.getElementById('particles');
      for (let i = 0; i < 30; i++) {
        const particle = document.createElement('div');
        particle.classList.add('particle');
        particle.style.left = Math.random() * 100 + '%';
        particle.style.animationDuration = Math.random() * 10 + 8 + 's';
        particle.style.animationDelay = Math.random() * 10 + 's';
        particle.style.width = Math.random() * 3 + 1 + 'px';
        particle.style.height = particle.style.width;
        particlesContainer.appendChild(particle);
      }

      // Scroll reveal
      const observerOptions = {
        threshold: 0.1,
        rootMargin: '0px 0px -50px 0px',
      };

      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry, index) => {
          if (entry.isIntersecting) {
            setTimeout(() => {
              entry.target.classList.add('visible');
            }, index * 100);
            observer.unobserve(entry.target);
          }
        });
      }, observerOptions);

      document
        .querySelectorAll('.reveal, .reveal-left, .reveal-right')
        .forEach((el) => {
          observer.observe(el);
        });

      // Menu Data
      const menuItems = [
        {
          category: 'starters',
          name: 'Tuna Tartare',
          desc: 'Fresh yellowfin tuna, avocado mousse, sesame, wasabi aioli',
          price: 'KSh 2,800',
          img: 'https://images.unsplash.com/photo-1534604973900-c43ab4c2e0ab?w=500&q=80',
          rating: 5,
          badge: "Chef's Pick",
        },
        {
          category: 'starters',
          name: 'Truffle Soup',
          desc: 'Wild mushroom velouté, black truffle shavings, chive oil',
          price: 'KSh 1,900',
          img: 'https://images.unsplash.com/photo-1547592166-23ac45744acd?w=500&q=80',
          rating: 5,
          badge: '',
        },
        {
          category: 'starters',
          name: 'Calamari Fritti',
          desc: 'Crispy fried calamari, saffron aioli, citrus zest',
          price: 'KSh 2,200',
          img: 'https://images.unsplash.com/photo-1599487488170-d11ec9c172f0?w=500&q=80',
          rating: 4,
          badge: '',
        },
        {
          category: 'mains',
          name: 'Wagyu Ribeye',
          desc: 'A5 Japanese Wagyu, miso glaze, roasted vegetables, truffle jus',
          price: 'KSh 12,500',
          img: 'https://images.unsplash.com/photo-1546833999-b9f581a1996d?w=500&q=80',
          rating: 5,
          badge: 'Premium',
        },
        {
          category: 'mains',
          name: 'Pan-Seared Salmon',
          desc: 'Atlantic salmon, lemon butter, asparagus, herb risotto',
          price: 'KSh 4,800',
          img: 'https://images.unsplash.com/photo-1467003909585-2f8a72700288?w=500&q=80',
          rating: 5,
          badge: 'Best Seller',
        },
        {
          category: 'mains',
          name: 'Lamb Rack',
          desc: 'New Zealand lamb, mint pesto, root vegetable gratin',
          price: 'KSh 6,900',
          img: 'https://images.unsplash.com/photo-1600891964092-4316c288032e?w=500&q=80',
          rating: 5,
          badge: '',
        },
        {
          category: 'desserts',
          name: 'Chocolate Fondant',
          desc: 'Molten dark chocolate, vanilla bean ice cream, gold leaf',
          price: 'KSh 1,800',
          img: 'https://images.unsplash.com/photo-1551024506-0bccd828d307?w=500&q=80',
          rating: 5,
          badge: 'Signature',
        },
        {
          category: 'desserts',
          name: 'Tiramisu',
          desc: 'Classic Italian layers, espresso-soaked mascarpone, cocoa',
          price: 'KSh 1,500',
          img: 'https://images.unsplash.com/photo-1571877227200-a0d98ea607e9?w=500&q=80',
          rating: 4,
          badge: '',
        },
        {
          category: 'desserts',
          name: 'Mango Cheesecake',
          desc: 'Creamy cheesecake, tropical mango coulis, passion fruit',
          price: 'KSh 1,600',
          img: 'https://images.unsplash.com/photo-1565958011703-44f9829ba187?w=500&q=80',
          rating: 4,
          badge: '',
        },
        {
          category: 'drinks',
          name: 'Old Fashioned',
          desc: 'Bourbon, bitters, orange zest, demerara sugar',
          price: 'KSh 1,400',
          img: 'https://images.unsplash.com/photo-1470337458703-46ad1756a187?w=500&q=80',
          rating: 5,
          badge: '',
        },
        {
          category: 'drinks',
          name: 'Neshville Martini',
          desc: 'Gin, elderflower, cucumber, champagne float',
          price: 'KSh 1,600',
          img: 'https://images.unsplash.com/photo-1514362545857-3bc16c4c7d1b?w=500&q=80',
          rating: 5,
          badge: 'House Special',
        },
        {
          category: 'drinks',
          name: 'Rosé Selection',
          desc: 'Premium rosé flights from Provence & South Africa',
          price: 'KSh 2,200',
          img: 'https://images.unsplash.com/photo-1558618666-fcd25c85f82e?w=500&q=80',
          rating: 4,
          badge: '',
        },
      ];

      function renderMenu(category = 'all') {
        const grid = document.getElementById('menuGrid');
        const filtered =
          category === 'all'
            ? menuItems
            : menuItems.filter((item) => item.category === category);

        grid.innerHTML = filtered
          .map(
            (item, i) => `
                <div class="menu-card" style="transition-delay: ${i * 0.1}s">
                    <div class="menu-card-img">
                        <img src="${item.img}" alt="${item.name}" loading="lazy">
                        ${item.badge ? `<div class="menu-card-badge">${item.badge}</div>` : ''}
                    </div>
                    <div class="menu-card-body">
                        <div class="menu-card-top">
                            <h3>${item.name}</h3>
                            <div class="menu-card-price">${item.price}</div>
                        </div>
                        <p>${item.desc}</p>
                        <div class="menu-card-bottom">
                            <div class="menu-card-rating">
                                ${'<i class="fas fa-star"></i>'.repeat(item.rating)}${'<i class="far fa-star"></i>'.repeat(5 - item.rating)}
                            </div>
                            <button class="menu-card-add"><i class="fas fa-plus"></i></button>
                        </div>
                    </div>
                </div>
            `,
          )
          .join('');

        // Re-observe new cards
        setTimeout(() => {
          grid.querySelectorAll('.menu-card').forEach((card, idx) => {
            setTimeout(() => card.classList.add('visible'), idx * 100);
          });
        }, 50);
      }

      renderMenu();

      // Menu tabs
      document.querySelectorAll('.menu-tab').forEach((tab) => {
        tab.addEventListener('click', () => {
          document
            .querySelectorAll('.menu-tab')
            .forEach((t) => t.classList.remove('active'));
          tab.classList.add('active');
          renderMenu(tab.dataset.category);
        });
      });

      // Testimonials Slider
      let currentSlide = 0;
      const track = document.getElementById('testimonialsTrack');
      const dots = document.querySelectorAll('.testimonial-dot');

      function goToSlide(index) {
        currentSlide = index;
        track.style.transform = `translateX(-${index * 100}%)`;
        dots.forEach((dot, i) => {
          dot.classList.toggle('active', i === index);
        });
      }

      dots.forEach((dot) => {
        dot.addEventListener('click', () => {
          goToSlide(parseInt(dot.dataset.index));
        });
      });

      // Auto slide
      setInterval(() => {
        currentSlide = (currentSlide + 1) % 3;
        goToSlide(currentSlide);
      }, 5000);

      // Gallery Lightbox
      const lightbox = document.getElementById('lightbox');
      const lightboxImg = document.getElementById('lightboxImg');
      const lightboxClose = document.getElementById('lightboxClose');

      document.querySelectorAll('.gallery-item').forEach((item) => {
        item.addEventListener('click', () => {
          const src = item.dataset.src;
          lightboxImg.src = src;
          lightbox.classList.add('active');
          document.body.style.overflow = 'hidden';
        });
      });

      lightboxClose.addEventListener('click', () => {
        lightbox.classList.remove('active');
        document.body.style.overflow = '';
      });

      lightbox.addEventListener('click', (e) => {
        if (e.target === lightbox) {
          lightbox.classList.remove('active');
          document.body.style.overflow = '';
        }
      });

      document.addEventListener('keydown', (e) => {
        if (e.key === 'Escape' && lightbox.classList.contains('active')) {
          lightbox.classList.remove('active');
          document.body.style.overflow = '';
        }
      });

      // Back to Top
      const backToTop = document.getElementById('backToTop');
      window.addEventListener('scroll', () => {
        if (window.scrollY > 500) {
          backToTop.classList.add('show');
        } else {
          backToTop.classList.remove('show');
        }
      });

      backToTop.addEventListener('click', () => {
        window.scrollTo({ top: 0, behavior: 'smooth' });
      });

      // Form submission
      document.getElementById('bookingForm').addEventListener('submit', (e) => {
        e.preventDefault();
        const btn = e.target.querySelector('.btn-primary');
        const originalText = btn.textContent;
        btn.textContent = 'Reservation Confirmed ✓';
        btn.style.background = '#2d5a3d';
        btn.style.color = '#fff';
        setTimeout(() => {
          btn.textContent = originalText;
          btn.style.background = '';
          btn.style.color = '';
          e.target.reset();
        }, 3000);
      });

      // Counter animation for about section
      function animateCounters() {
        const counters = document.querySelectorAll('.about-exp .number');
        counters.forEach((counter) => {
          const target = parseInt(counter.textContent);
          let current = 0;
          const increment = target / 40;
          const timer = setInterval(() => {
            current += increment;
            if (current >= target) {
              counter.textContent = target + '+';
              clearInterval(timer);
            } else {
              counter.textContent = Math.ceil(current) + '+';
            }
          }, 40);
        });
      }

      const expObserver = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              animateCounters();
              expObserver.unobserve(entry.target);
            }
          });
        },
        { threshold: 0.5 },
      );

      const expEl = document.querySelector('.about-exp');
      if (expEl) expObserver.observe(expEl);

      // Smooth scroll for anchor links
      document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
        anchor.addEventListener('click', function (e) {
          e.preventDefault();
          const target = document.querySelector(this.getAttribute('href'));
          if (target) {
            target.scrollIntoView({ behavior: 'smooth', block: 'start' });
          }
        });
      });

      // Set min date for booking
      const dateInput = document.querySelector('input[type="date"]');
      if (dateInput) {
        const today = new Date().toISOString().split('T')[0];
        dateInput.min = today;
      }
    </script>
  </body>
</html>
