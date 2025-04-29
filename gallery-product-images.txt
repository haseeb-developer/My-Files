// Too add this file you have to create a section like "gallery-product-images.liquid" and paste the following code.
// And then in main-product.liquid you have to put this because u have to render the section u created. render {{ gallery-product-images.liquid }} then it will work.
// This section has zoom effect on image like amazon, Plus it has the gallery feature.





<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css">

<style>
    @import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@300..700&family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&family=Manrope:wght@200..800&family=Montserrat:ital,wght@0,100..900;1,100..900&family=Open+Sans:ital,wght@0,300..800;1,300..800&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Quicksand:wght@300..700&family=Ubuntu:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&family=Work+Sans:ital,wght@0,100..900;1,100..900&display=swap');

    #product-gallery-container-{{ product.id }} .product_slider {
      width: 100%;
      height: 100%;
    }

    #product-gallery-container-{{ product.id }} .product-gallery-container {
      gap: 40px;
      margin: 0 auto;
      flex-direction: row;
    }

    #product-gallery-container-{{ product.id }} .product-gallery {
      display: flex;
      flex-direction: column;
      gap: 15px;
      max-width: 100%;
      width: 100%;
      padding: 0;
      flex-shrink: 0;
    }

    #product-gallery-container-{{ product.id }} .product_slider {
      width: 100%;
      height: auto;
      aspect-ratio: 1/1;
      position: relative;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
      background: #fff;
    }

    #product-gallery-container-{{ product.id }} .product_slider .swiper-wrapper {
      width: 100%;
      height: 100%;
    }

    #product-gallery-container-{{ product.id }} .product_slider .swiper-slide {
      display: flex;
      align-items: center;
      justify-content: center;
      background: #d8d8d8;
    }

    #product-gallery-container-{{ product.id }} .product_slider .swiper-slide img,
    #product-gallery-container-{{ product.id }} .product_slider .swiper-slide video {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    #product-gallery-container-{{ product.id }} .thumbnails-column {
      width: 100%;
    }



    /* #product-gallery-container-{{ product.id }} .thumbnail-item {
      width: 80px;
      height: 80px;
      flex-shrink: 0;
      cursor: pointer;
      position: relative;
      border-radius: 8px;
      overflow: hidden;
      border: 2px solid transparent;
      transition: all 0.3s ease;
      opacity: 0.5;
    } */

    /* #product-gallery-container-{{ product.id }} .thumbnail-item::after {
      content: '';
      position: absolute;
      inset: 0;
      background: rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    } */

    #product-gallery-container-{{ product.id }} .thumbnail-item:hover {
      transform: translateY(-2px);
      opacity: 0.8;
      filter: grayscale(20%) blur(0px);
    }

    #product-gallery-container-{{ product.id }} .thumbnail-item.active {
      border: 2px solid #071f60;
      opacity: 1;
      filter: none;
      box-shadow: 0 4px 12px rgba(76, 175, 80, 0.3);
    }

    #product-gallery-container-{{ product.id }} .thumbnail-item.active::after {
      background: transparent;
    }

    #product-gallery-container-{{ product.id }} .thumbnail-item img,
    #product-gallery-container-{{ product.id }} .thumbnail-item video {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: all 0.2s ease;
    }

    #product-gallery-container-{{ product.id }}  .thumbnail-item img {
      border-radius: 12px;
    }

    #product-gallery-container-{{ product.id }} .product-info {
      flex: 1;
      min-width: 300px;
      max-width: 45%;
      padding: 0;
    }

    #product-gallery-container-{{ product.id }} .nav-button {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      width: 40px;
      height: 40px;
      background: rgba(255, 255, 255, 0.95);
      border-radius: 50%;
      z-index: 10;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
      transition: all 0.3s ease;
      border: none;
      opacity: 0;
      visibility: hidden;
    }

    #product-gallery-container-{{ product.id }} .nav-button:hover {
      border: 2px solid #fff;
      background-color: transparent;
      color: #fff;
    }

    #product-gallery-container-{{ product.id }} .nav-button svg {
      width: 24px;
      height: 24px;
      fill: #333;
    }

    #product-gallery-container-{{ product.id }} .nav-button:hover svg {
      fill: #fff;
    }

    #product-gallery-container-{{ product.id }} .nav-button.prev {
      left: -48px;
      transition: left 0.3s ease, opacity 0.3s ease, visibility 0.3s ease, transform 0.3s ease, background-color 0.3s ease,
        box-shadow 0.3s ease;
    }

    #product-gallery-container-{{ product.id }} .nav-button.next {
      right: -48px;
      transition: right 0.3s ease, opacity 0.3s ease, visibility 0.3s ease, transform 0.3s ease,
        background-color 0.3s ease, box-shadow 0.3s ease;
    }

    #product-gallery-container-{{ product.id }} .product_slider:hover .nav-button {
      opacity: 1;
      visibility: visible;
    }

    #product-gallery-container-{{ product.id }} .product_slider:hover .nav-button.prev {
      left: 20px;
    }

    #product-gallery-container-{{ product.id }} .product_slider:hover .nav-button.next {
      right: 20px;
    }

    #product-gallery-container-{{ product.id }} iframe {
      max-width: 100%;
      width: 100%;
      height: 100%;
    }

    #product-gallery-container-{{ product.id }} .gallery-instruction {
      text-align: center;
      margin: 0;
      padding: 0;
    }

    #product-gallery-container-{{ product.id }} .gallery-instruction p {
      margin: 0;
      padding: 0;
      color: #071f60;
      font-family: 'Poppins', sans-serif;
      line-height: 1.5;
      font-size: 14px;
    }

    #product-gallery-container-{{ product.id }} .zoom-container {
      overflow: hidden;
      position: relative;
      width: 100%;
      height: 100%;
      cursor: zoom-in;
    }

    #product-gallery-container-{{ product.id }} .zoom-image {
      transition: transform 0.1s ease;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    @media (max-width: 1200px) {
      #product-gallery-container-{{ product.id }} .product.grid.grid--1-col.product--sticky {
        display: block;
      }

      #product-gallery-container-{{ product.id }} .grid__item.product__media-wrapper {
        max-width: 100%;
        width: 100%;
      }

      #product-gallery-container-{{ product.id }} .product-gallery {
        display: flex;
        justify-content: center;
        max-width: 100%;
        width: 100%;
      }

      #product-gallery-container-{{ product.id }} .grid__item.product__info-wrapper {
        max-width: 100%;
        width: 100%;
        margin-top: 50px;
        padding-left: 0;
      }
    }

    #product-gallery-container-{{ product.id }} .swiper-slide-thumb-active {
      border: 3px solid rgb(3, 3, 3);
      border-radius: 16px;
      padding: 0;
      margin: 0;
    }

    #product-gallery-container-{{ product.id }} .video-container {
      max-width: 100%;
      width: 100%;
      height: 100%;
  }

   #product-gallery-container-{{ product.id }} .thumbnail-item {
       transition: all 0.3s ease;
       max-width: 130px;
        width: 100%;
      height: 80px;
      cursor: pointer;
    }

    #product-gallery-container-{{ product.id }} .video-input {
      width: 100%;
      height: 100%;
      background: #f4f4f4;
      display: flex;
      align-items: center;
      justify-content: center;
    }
</style>

<div class="product-gallery-container" id="product-gallery-container-{{ product.id }}">
  <div class="product-gallery">
    <div class="swiper product_slider">
      <div class="swiper-wrapper">
        {%- for media in product.media -%}
          <div class="swiper-slide">
            {% case media.media_type %}
              {% when 'image' %}
                <div class="zoom-container">
                  <img
                    src="{{ media | image_url: width: 1200 }}"
                    alt="{{ media.alt | escape }}"
                    loading="lazy"
                    class="zoom-image"
                  >
                </div>
              {% when 'external_video' %}
                <div class="video-container">
                  {{ media | external_video_tag: class: 'product-video' }}
                </div>
              {% when 'video' %}
                <div class="video-container">
                  {{ media | video_tag: controls: true, class: 'product-video' }}
                </div>
            {% endcase %}
          </div>
        {%- endfor -%}
      </div>

      <button class="nav-button prev" aria-label="Previous slide">
        <svg viewBox="0 0 24 24">
          <path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12z"/>
        </svg>
      </button>
      <button class="nav-button next" aria-label="Next slide">
        <svg viewBox="0 0 24 24">
          <path d="M8.59 16.59L10 18l6-6-6-6-1.41 1.41L13.17 12z"/>
        </svg>
      </button>
    </div>

    <div class="gallery-instruction">
      <p>Hover over image to zoom</p>
    </div>

    <div class="thumbnails-column swiper">
      <div class="swiper-wrapper">
        {%- for media in product.media -%}
          <div class="thumbnail-item swiper-slide" data-index="{{ forloop.index0 }}">
            {% case media.media_type %}
              {% when 'image' %}
                <img
                  src="{{ media | image_url: width: 240 }}"
                  alt="{{ media.alt | escape }}"
                  loading="lazy"
                >
              {% when 'external_video' %}
                {% if media.host == 'youtube' %}
                  <img
                    src="https://img.youtube.com/vi/{{ media.external_id }}/default.jpg"
                    loading="lazy"
                    alt="Video thumbnail"
                  >
                {% else %}
                  <div class="video-input">Video</div>
                {% endif %}
              {% when 'video' %}
                <div class="video-input">Video</div>
            {% endcase %}
          </div>
        {%- endfor -%}
      </div>
    </div>
  </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>

<script>
  document.addEventListener('DOMContentLoaded', function () {
    var thumbSwiper = new Swiper('.thumbnails-column', {
      loop: false,
      spaceBetween: 10,
      slidesPerView: 6,
      freeMode: true,
      watchSlidesProgress: true,
    });

    var mainSwiper = new Swiper('.product_slider', {
      loop: false,
      spaceBetween: 10,
      speed: 500,
      thumbs: {
        swiper: thumbSwiper,
      },
      effect: 'fade',
      fadeEffect: {
        crossFade: true,
      },
      navigation: {
        nextEl: '.nav-button.next',
        prevEl: '.nav-button.prev',
      },
    });

    document.querySelectorAll('.thumbnail-item').forEach((thumb) => {
      thumb.addEventListener('click', function () {
        const index = parseInt(this.getAttribute('data-index'));
        mainSwiper.slideTo(index);
      });
    });

    mainSwiper.on('slideChange', function () {
      document.querySelectorAll('.thumbnail-item').forEach((thumb) => {
        thumb.classList.remove('active');
      });
      const activeThumb = document.querySelector(`.thumbnail-item[data-index="${mainSwiper.realIndex}"]`);
      if (activeThumb) {
        activeThumb.classList.add('active');
      }
    });

    document.querySelector('.thumbnail-item[data-index="0"]')?.classList.add('active');

    document.querySelectorAll('.zoom-container').forEach((container) => {
      const img = container.querySelector('.zoom-image');
      container.addEventListener('mousemove', (e) => {
        const { left, top, width, height } = container.getBoundingClientRect();
        const x = (e.clientX - left) / width;
        const y = (e.clientY - top) / height;
        img.style.transformOrigin = `${x * 100}% ${y * 100}%`;
        img.style.transform = 'scale(2)';
      });
      container.addEventListener('mouseleave', () => {
        img.style.transform = 'scale(1)';
        img.style.transformOrigin = 'center';
      });
    });
  });
</script>
