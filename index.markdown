---
layout: common
permalink: /
---

<head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Exp-Force: Experience-Conditioned Pre-Grasp Force Selection with Vision-Language Models</title>
  <meta property="og:title" content="Exp-Force">
  <meta property="og:description" content="An experience-conditioned framework that predicts minimum feasible grasping force from a single RGB image.">

  <link href="https://fonts.googleapis.com/css?family=Titillium+Web:400,600,400italic,600italic,300,300italic" rel="stylesheet" type="text/css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/jpswalsh/academicons@1/css/academicons.min.css">
  <script src="https://kit.fontawesome.com/ef67f68cfb.js" crossorigin="anonymous"></script>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      const videos = document.querySelectorAll('video.lazy-video');
      const observer = new IntersectionObserver(entries => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.play();
          } else {
            entry.target.pause();
          }
        });
      }, { threshold: 0.5 });
      videos.forEach(video => observer.observe(video));

      const modal = document.querySelector('[data-image-modal]');
      const modalImage = document.querySelector('[data-image-modal-content]');
      const modalCaption = document.querySelector('[data-image-modal-caption]');
      const modalClose = document.querySelector('[data-image-modal-close]');

      if (modal && modalImage && modalCaption && modalClose) {
        const openModal = (src, alt) => {
          modalImage.src = src;
          modalImage.alt = alt;
          modalCaption.textContent = alt;
          modal.hidden = false;
          document.body.style.overflow = 'hidden';
        };

        const closeModal = () => {
          modal.hidden = true;
          modalImage.removeAttribute('src');
          modalImage.alt = '';
          modalCaption.textContent = '';
          document.body.style.overflow = '';
        };

        document.querySelectorAll('[data-enlarge-image]').forEach(link => {
          link.addEventListener('click', event => {
            event.preventDefault();
            openModal(link.href, link.dataset.imageAlt || 'Dataset image');
          });
        });

        modal.addEventListener('click', event => {
          if (event.target === modal || event.target === modalClose) {
            closeModal();
          }
        });

        document.addEventListener('keydown', event => {
          if (event.key === 'Escape' && !modal.hidden) {
            closeModal();
          }
        });
      }
    });
  </script>

  <style type="text/css" media="all">
    body {
      font-family: "Titillium Web", "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif;
      font-weight: 300;
      font-size: 18px;
      margin-left: auto;
      margin-right: auto;
      width: 100%;
      text-align: center;
    }
    h1 { font-weight: 300; }
    h2 { font-weight: 300; font-size: 24px; }
    h3 { font-weight: 300; }
    a {
      color: #005577;
      text-decoration: none;
      font-weight: 500;
    }
    a:hover { text-decoration: underline; }
    #primarycontent {
      margin-left: auto;
      margin-right: auto;
      text-align: left;
      max-width: 1000px;
    }
    IMG {
      padding: 0;
      display: block;
      margin: auto;
    }
    hr {
      border: 0;
      height: 1px;
      max-width: 1100px;
      background-image: linear-gradient(to right, rgba(0,0,0,0), rgba(0,0,0,0.75), rgba(0,0,0,0));
    }
    pre {
      background: #f4f4f4;
      border: 1px solid #ddd;
      color: #666;
      font-family: monospace;
      font-size: 15px;
      line-height: 1.6;
      margin-bottom: 1.6em;
      max-width: 100%;
      overflow: auto;
      padding: 10px;
      display: block;
      word-wrap: break-word;
    }
    .badge {
      display: inline-block;
      margin: 4px;
      padding: 6px 14px;
      border-radius: 4px;
      font-size: 16px;
      font-weight: 500;
      background: #f0f4f8;
      border: 1px solid #c8d6e5;
    }
    .result-highlight {
      color: #c0392b;
      font-weight: 600;
    }
    .dataset-summary {
      max-width: 800px;
      margin: 0 auto 12px;
      text-align: justify;
    }
    .dataset-details {
      max-width: 900px;
      margin: 0 auto;
      border: 1px solid #d9e2ec;
      border-radius: 8px;
      background: #fafcff;
      overflow: hidden;
    }
    .dataset-details summary {
      cursor: pointer;
      list-style: none;
      padding: 14px 18px;
      font-size: 18px;
      font-weight: 600;
      text-align: left;
      background: #f0f4f8;
    }
    .dataset-details summary::-webkit-details-marker {
      display: none;
    }
    .dataset-details summary::after {
      content: "+";
      float: right;
      font-size: 22px;
      line-height: 1;
    }
    .dataset-details[open] summary::after {
      content: "\2212";
    }
    .dataset-table-wrap {
      overflow-x: auto;
      padding: 0 18px 18px;
    }
    .dataset-table {
      width: 100%;
      border-collapse: collapse;
      min-width: 640px;
      background: #ffffff;
    }
    .dataset-table th,
    .dataset-table td {
      padding: 10px 12px;
      border-bottom: 1px solid #e6ecf2;
      vertical-align: middle;
    }
    .dataset-table th {
      text-align: left;
      background: #f8fafc;
      font-weight: 600;
    }
    .dataset-table td.dataset-number {
      white-space: nowrap;
    }
    .dataset-thumb-link {
      display: inline-block;
      cursor: zoom-in;
    }
    .dataset-thumb {
      width: 72px;
      height: 72px;
      object-fit: cover;
      border-radius: 6px;
      border: 1px solid #d9e2ec;
      background: #ffffff;
    }
    .image-modal {
      position: fixed;
      inset: 0;
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px;
      background: rgba(10, 20, 30, 0.82);
    }
    .image-modal[hidden] {
      display: none;
    }
    .image-modal-dialog {
      position: relative;
      max-width: min(92vw, 980px);
      max-height: 92vh;
      padding: 18px 18px 14px;
      border-radius: 12px;
      background: #ffffff;
      box-shadow: 0 18px 60px rgba(0, 0, 0, 0.28);
    }
    .image-modal-close {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 36px;
      height: 36px;
      border: 0;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.08);
      color: #111827;
      font-size: 28px;
      line-height: 1;
      cursor: pointer;
    }
    .image-modal-close:hover {
      background: rgba(15, 23, 42, 0.14);
    }
    .image-modal-image {
      max-width: 100%;
      max-height: calc(92vh - 90px);
      border-radius: 8px;
      object-fit: contain;
    }
    .image-modal-caption {
      margin-top: 10px;
      text-align: center;
      font-weight: 600;
    }
    @media (max-width: 700px) {
      .dataset-details summary {
        font-size: 17px;
      }
      .dataset-table th,
      .dataset-table td {
        padding: 8px 10px;
        font-size: 15px;
      }
      .dataset-thumb {
        width: 56px;
        height: 56px;
      }
      .image-modal {
        padding: 12px;
      }
      .image-modal-dialog {
        padding: 14px 14px 12px;
      }
    }
  </style>
</head>

<body>
<div id="primarycontent">
  <div style="height: 12px;"></div>

  <center>
    <h1>
      <strong>Exp-Force: Experience-Conditioned Pre-Grasp<br>Force Selection with Vision-Language Models</strong>
    </h1>
  </center>

  <center>
    <h3>
      <!-- TODO: Uncomment and update when paper/code are available -->
      <!-- <a href="#"><i class="ai ai-arxiv"></i> Paper</a> | -->
      <!-- <a href="#"><i class="fa-brands fa-github"></i> Code</a> -->
    </h3>
  </center>

  <p>
    <table align="center" width="800px">
      <tr>
        <td>
          <p align="justify">
            Accurate pre-contact grasp force selection is critical for safe and reliable robotic manipulation.
            Adaptive controllers regulate force after contact but still require a reasonable initial estimate.
            Starting a grasp with too little force requires reactive adjustment, while starting with too high a
            force risks damaging fragile objects. This trade-off is particularly challenging for compliant grippers,
            whose contact mechanics are difficult to model analytically.
          </p>
          <p align="justify">
            We propose <strong>Exp-Force</strong>, an experience-conditioned framework that predicts the minimum
            feasible grasping force from a single RGB image. The method retrieves a small set of relevant prior
            grasping experiences and conditions a vision&ndash;language model on these examples for in-context
            inference, without analytic contact models or manually designed heuristics.
          </p>
          <p align="justify">
            On 129 object instances, Exp-Force achieves a best-case MAE of <span class="result-highlight">0.426&thinsp;N</span>,
            reducing error by <span class="result-highlight">72%</span> over zero-shot inference. In real-world
            tests on 30 unseen objects, it improves appropriate force selection from 67% to
            <span class="result-highlight">91%</span>.
          </p>
        </td>
      </tr>
    </table>
  </p>

  <center><h2>Zero-shot vs Exp-Force</h2></center>
  <table border="0" cellspacing="10" cellpadding="0" align="center" width="800px">
    <tbody>
      <tr>
        <td align="center" valign="middle">
          <video muted autoplay loop playsinline width="100%" style="border-radius: 4px;">
            <source src="{{ '/src/video/cheez-it.mp4' | relative_url }}" type="video/mp4">
          </video>
        </td>
      </tr>
      <tr>
        <td align="center" valign="top"><p style="font-size: 16px; margin: 0; padding-bottom: 20px;">Cheez-It Box</p></td>
      </tr>
      <tr>
        <td align="center" valign="middle">
          <video muted autoplay loop playsinline width="100%" style="border-radius: 4px;">
            <source src="{{ '/src/video/champagne-glass.mp4' | relative_url }}" type="video/mp4">
          </video>
        </td>
      </tr>
      <tr>
        <td align="center" valign="top"><p style="font-size: 16px; margin: 0;">Champagne Glass</p></td>
      </tr>
    </tbody>
  </table>

  <br>

  <center><h2>Grasping Fragile and Light Objects</h2></center>
  <table border="0" cellspacing="10" cellpadding="0" align="center" width="800px">
    <tbody>
      <tr>
        <td align="center" valign="middle">
          <video muted autoplay loop playsinline width="100%" style="border-radius: 4px;">
            <source src="{{ '/src/video/Fragile-Light.mp4' | relative_url }}" type="video/mp4">
          </video>
        </td>
      </tr>
      <tr></tr>
    </tbody>
  </table>

  <br>

  <center><h2>Grasping Fragile and Heavy Objects</h2></center>
  <table border="0" cellspacing="10" cellpadding="0" align="center" width="800px">
    <tbody>
      <tr>
        <td align="center" valign="middle">
          <video muted autoplay loop playsinline width="100%" style="border-radius: 4px;">
            <source src="{{ '/src/video/Fragile-Heavy.mp4' | relative_url }}" type="video/mp4">
          </video>
        </td>
      </tr>
      <tr></tr>
    </tbody>
  </table>

  <br>

  <center><h2>Grasping Bottle and Odd Objects</h2></center>
  <table border="0" cellspacing="10" cellpadding="0" align="center" width="800px">
    <tbody>
      <tr>
        <td align="center" valign="middle">
          <video muted autoplay loop playsinline width="100%" style="border-radius: 4px;">
            <source src="{{ '/src/video/Bottles & Odd.mp4' | relative_url }}" type="video/mp4">
          </video>
        </td>
      </tr>
      <tr></tr>
    </tbody>
  </table>

  <br>

  <center><h2>Dataset</h2></center>
  {% assign dataset_rows = site.data.dataset | default: empty %}
  {% assign dataset_count = dataset_rows | size %}
  <p class="dataset-summary">
    The dataset contains {{ dataset_count }} object instances used to study pre-grasp force prediction.
    Each entry includes the object image, its measured mass in grams, and the minimum feasible grasping force in newtons.
    Expand the table below to browse the full dataset and inspect each object image directly.
    Click any thumbnail to enlarge it without leaving the page.
  </p>
  <details class="dataset-details">
    <summary>View full dataset ({{ dataset_count }} objects)</summary>
    <div class="dataset-table-wrap">
      <table class="dataset-table">
        <thead>
          <tr>
            <th>Image</th>
            <th>Object</th>
            <th>Mass [g]</th>
            <th>Grasp Force [N]</th>
          </tr>
        </thead>
        <tbody>
          {% if dataset_count > 0 %}
          {% for item in dataset_rows %}
          {% assign image_path = '/images/' | append: item["Image"] %}
          <tr>
            <td>
              <a class="dataset-thumb-link" href="{{ image_path | relative_url }}" data-enlarge-image data-image-alt="{{ item['Object'] }}">
                <img
                  class="dataset-thumb"
                  src="{{ image_path | relative_url }}"
                  alt="{{ item['Object'] }}"
                  loading="lazy">
              </a>
            </td>
            <td>{{ item["Object"] }}</td>
            <td class="dataset-number">{{ item["Mass"] }}</td>
            <td class="dataset-number">{{ item["Gripping Force"] }}</td>
          </tr>
          {% endfor %}
          {% else %}
          <tr>
            <td colspan="4">Dataset entries are currently unavailable.</td>
          </tr>
          {% endif %}
        </tbody>
      </table>
    </div>
  </details>

  <div style="height: 40px;"></div>
</div>
<div class="image-modal" data-image-modal hidden>
  <div class="image-modal-dialog" role="dialog" aria-modal="true" aria-labelledby="image-modal-caption">
    <button class="image-modal-close" type="button" aria-label="Close enlarged image" data-image-modal-close>&times;</button>
    <img class="image-modal-image" data-image-modal-content alt="">
    <div class="image-modal-caption" id="image-modal-caption" data-image-modal-caption></div>
  </div>
</div>
</body>
