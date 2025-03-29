<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>DesignNav - Your Personal Design Resources</title>
  <style>
    :root {
      --primary: #4285f4;
      --primary-light: #e8f0fe;
      --text-dark: #333;
      --text-light: #666;
      --white: #fff;
      --border: #e1e4e8;
      --shadow: rgba(0, 0, 0, 0.05);
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    
    body {
      background-color: #f8f9fa;
      color: var(--text-dark);
      line-height: 1.6;
    }
    
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 20px;
    }
    
    header {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-bottom: 40px;
      padding-top: 30px;
    }
    
    .logo {
      font-size: 28px;
      font-weight: 700;
      color: var(--primary);
      margin-bottom: 20px;
    }
    
    .search-container {
      width: 100%;
      max-width: 600px;
      margin-bottom: 20px;
    }
    
    .search-bar {
      display: flex;
      width: 100%;
      border: 1px solid var(--border);
      border-radius: 24px;
      overflow: hidden;
      box-shadow: 0 2px 5px var(--shadow);
      background: var(--white);
    }
    
    .search-bar input {
      flex-grow: 1;
      padding: 12px 16px;
      border: none;
      outline: none;
      font-size: 16px;
    }
    
    .search-bar button {
      background: var(--primary);
      color: white;
      border: none;
      padding: 0 20px;
      cursor: pointer;
      font-size: 16px;
    }
    
    .grid-container {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
      margin-bottom: 40px;
    }
    
    @media (max-width: 768px) {
      .grid-container {
        grid-template-columns: 1fr;
      }
    }
    
    .grid-item {
      background: var(--white);
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 4px 6px var(--shadow);
    }
    
    .category-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;
      padding-bottom: 10px;
      border-bottom: 1px solid var(--border);
    }
    
    .category-title {
      font-size: 18px;
      font-weight: 600;
      color: var(--primary);
    }
    
    .see-more {
      font-size: 14px;
      color: var(--primary);
      cursor: pointer;
      display: flex;
      align-items: center;
    }
    
    .sites-container {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 12px;
    }
    
    @media (max-width: 576px) {
      .sites-container {
        grid-template-columns: 1fr;
      }
    }
    
    .site-card {
      display: flex;
      align-items: center;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid var(--border);
      transition: transform 0.2s, box-shadow 0.2s;
    }
    
    .site-card:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 8px var(--shadow);
      border-color: var(--primary-light);
    }
    
    .site-logo {
      width: 40px;
      height: 40px;
      border-radius: 8px;
      margin-right: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--primary-light);
      color: var(--primary);
      font-weight: bold;
      font-size: 18px;
    }
    
    .site-info {
      flex-grow: 1;
    }
    
    .site-title {
      font-weight: 600;
      font-size: 14px;
      margin-bottom: 2px;
      color: var(--text-dark);
    }
    
    .site-desc {
      font-size: 12px;
      color: var(--text-light);
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    
    .favorite-btn {
      width: 22px;
      height: 22px;
      background: transparent;
      border: none;
      cursor: pointer;
      opacity: 0.3;
      transition: opacity 0.2s;
    }
    
    .favorite-btn:hover, .favorite-btn.active {
      opacity: 1;
    }
    
    .favorite-btn.active svg path {
      fill: gold;
    }
    
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 1000;
      align-items: center;
      justify-content: center;
    }
    
    .modal-content {
      background: var(--white);
      border-radius: 10px;
      padding: 20px;
      max-width: 800px;
      width: 90%;
      max-height: 80vh;
      overflow-y: auto;
    }
    
    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      padding-bottom: 10px;
      border-bottom: 1px solid var(--border);
    }
    
    .modal-title {
      font-size: 20px;
      font-weight: 600;
    }
    
    .close-button {
      background: transparent;
      border: none;
      font-size: 24px;
      cursor: pointer;
    }
    
    .modal-sites {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 15px;
    }
    
    .recommendations {
      margin-top: 40px;
    }
    
    .recommendations-header {
      font-size: 20px;
      font-weight: 600;
      margin-bottom: 20px;
      color: var(--primary);
      text-align: center;
    }
    
    .recommendations-container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 15px;
    }
    
    footer {
      text-align: center;
      margin-top: 40px;
      padding: 20px 0;
      color: var(--text-light);
      font-size: 14px;
    }
    
    .hidden {
      display: none;
    }
    
    .favorites-indicator {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: var(--primary);
      color: white;
      padding: 10px 15px;
      border-radius: 50px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    
    .favorites-count {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      background: white;
      color: var(--primary);
      width: 24px;
      height: 24px;
      border-radius: 50%;
      font-size: 12px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="logo">DesignNav</div>
      <div class="search-container">
        <form class="search-bar" action="https://www.google.com/search" method="get" target="_blank">
          <input type="text" name="q" placeholder="Search design resources..." id="search-input">
          <input type="hidden" name="sitesearch" value="">
          <button type="submit">Search</button>
        </form>
      </div>
    </header>
    
    <div class="grid-container">
      <!-- Design Tools -->
      <div class="grid-item">
        <div class="category-header">
          <div class="category-title">设计工具</div>
          <div class="see-more" onclick="openModal('design-tools-modal')">更多 +</div>
        </div>
        <div class="sites-container">
          <div class="site-card" data-id="svgomg">
            <div class="site-logo" style="background: #F44336; color: white;">S</div>
            <div class="site-info">
              <div class="site-title">SVGOMG</div>
              <div class="site-desc">在线SVG压缩平台</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('svgomg')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="android9">
            <div class="site-logo" style="background: #3DDC84; color: white;">A</div>
            <div class="site-info">
              <div class="site-title">Android 9</div>
              <div class="site-desc">阴影生成器</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('android9')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="tableconvert">
            <div class="site-logo" style="background: #2196F3; color: white;">T</div>
            <div class="site-info">
              <div class="site-title">表格工具</div>
              <div class="site-desc">在线表编辑工具</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('tableconvert')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="wappalyzer">
            <div class="site-logo" style="background: #673AB7; color: white;">W</div>
            <div class="site-info">
              <div class="site-title">Wappalyzer</div>
              <div class="site-desc">识别网站技术</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('wappalyzer')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
        </div>
      </div>
      
      <!-- Design News -->
      <div class="grid-item">
        <div class="category-header">
          <div class="category-title">设计资讯</div>
          <div class="see-more" onclick="openModal('design-news-modal')">更多 +</div>
        </div>
        <div class="sites-container">
          <div class="site-card" data-id="usepanda">
            <div class="site-logo" style="background: #FF9800; color: white;">P</div>
            <div class="site-info">
              <div class="site-title">Usepanda</div>
              <div class="site-desc">设计新闻阅读器</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('usepanda')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="mustsee">
            <div class="site-logo" style="background: #4CAF50; color: white;">M</div>
            <div class="site-info">
              <div class="site-title">Mustsee</div>
              <div class="site-desc">世界美景发现</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('mustsee')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="topys">
            <div class="site-logo" style="background: #FF5722; color: white;">T</div>
            <div class="site-info">
              <div class="site-title">Topys</div>
              <div class="site-desc">创意内容平台</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('topys')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="loftcn">
            <div class="site-logo" style="background: #795548; color: white;">L</div>
            <div class="site-info">
              <div class="site-title">Loftcn</div>
              <div class="site-desc">设计风向平台</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('loftcn')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
        </div>
      </div>
      
      <!-- Creative Tools -->
      <div class="grid-item">
        <div class="category-header">
          <div class="category-title">创意工具</div>
          <div class="see-more" onclick="openModal('creative-tools-modal')">更多 +</div>
        </div>
        <div class="sites-container">
          <div class="site-card" data-id="sizzy">
            <div class="site-logo" style="background: #9C27B0; color: white;">S</div>
            <div class="site-info">
              <div class="site-title">Sizzy</div>
              <div class="site-desc">Web开发者浏览工具</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('sizzy')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="csspeeper">
            <div class="site-logo" style="background: #607D8B; color: white;">C</div>
            <div class="site-info">
              <div class="site-title">CSSPeeper</div>
              <div class="site-desc">CSS洞察工具</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('csspeeper')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="aliued">
            <div class="site-logo" style="background: #E91E63; color: white;">A</div>
            <div class="site-info">
              <div class="site-title">阿里巴巴UBD</div>
              <div class="site-desc">品牌影像生成</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('aliued')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="iconpark">
            <div class="site-logo" style="background: #00BCD4; color: white;">I</div>
            <div class="site-info">
              <div class="site-title">IconPark</div>
              <div class="site-desc">免费图标资源库</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('iconpark')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
        </div>
      </div>
      
      <!-- Design Materials -->
      <div class="grid-item">
        <div class="category-header">
          <div class="category-title">设计素材</div>
          <div class="see-more" onclick="openModal('design-materials-modal')">更多 +</div>
        </div>
        <div class="sites-container">
          <div class="site-card" data-id="colorhunt">
            <div class="site-logo" style="background: #CDDC39; color: #333;">C</div>
            <div class="site-info">
              <div class="site-title">ColorHunt</div>
              <div class="site-desc">设计师调色板</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('colorhunt')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="flatuicolors">
            <div class="site-logo" style="background: #009688; color: white;">F</div>
            <div class="site-info">
              <div class="site-title">Flat UI Colors</div>
              <div class="site-desc">280种扁平化配色</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('flatuicolors')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="webgradients">
            <div class="site-logo" style="background: linear-gradient(45deg, #2196F3, #FF5722); color: white;">W</div>
            <div class="site-info">
              <div class="site-title">WebGradients</div>
              <div class="site-desc">180种渐变集合</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('webgradients')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
          <div class="site-card" data-id="materialui">
            <div class="site-logo" style="background: #8BC34A; color: white;">M</div>
            <div class="site-info">
              <div class="site-title">MaterialUI</div>
              <div class="site-desc">材料颜色设计</div>
            </div>
            <button class="favorite-btn" onclick="toggleFavorite('materialui')">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
    
    <div class="recommendations">
      <div class="recommendations-header">推荐网站</div>
      <div class="recommendations-container">
        <div class="site-card" data-id="unsplash">
          <div class="site-logo" style="background: #000; color: white;">U</div>
          <div class="site-info">
            <div class="site-title">Unsplash</div>
            <div class="site-desc">免费高质量图库</div>
          </div>
          <button class="favorite-btn" onclick="toggleFavorite('unsplash')">
            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
            </svg>
          </button>
        </div>
        <div class="site-card" data-id="figma">
          <div class="site-logo" style="background: #F24E1E; color: white;">F</div>
          <div class="site-info">
            <div class="site-title">Figma</div>
            <div class="site-desc">协作设计工具</div>
          </div>
          <button class="favorite-btn" onclick="toggleFavorite('figma')">
            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 18.26L4.94 22.23L6.52 14.33L0.5 9.27L8.61 8.5L12 1.27L15.39 8.5L23.5 9.27L17.48 14.33L19.06 22.23L12 18.26Z" fill="none" stroke="#000" stroke-width="1.5"/>
            </svg>
          </button>
        </div>
        <div class="site-card" data-id="behance">
          <div class="site-logo" style="background: #1769FF; color: white;">B</div>
          <div class="site-info">
            <div class="site-title">Behance</div>
            <div class="site-desc">设计作品展示平台</div>
          </div>
          <button class="favorite-btn" onclick="toggleFavorite('beh
