# UX & Performance Polish: Summary & Report

This document outlines the changes made to the website to improve user experience, accessibility, and performance.

## 1. Summary of Changes

The project focused on a comprehensive sweep of the site, addressing copy, design, structure, and performance.

-   **Codebase Refactoring:**
    -   The project was organized into a standard `assets/` directory structure.
    -   All inline CSS and JavaScript were externalized into `assets/css/style.css` and `assets/js/main.js` respectively.

-   **Copy & UX:**
    -   The Korean copy was revised for clarity, professionalism, and brand consistency, avoiding superlative claims.
    -   The HTML heading structure was corrected to a logical hierarchy (`H1` -> `H2`) for better accessibility and SEO.
    -   ARIA labels were added to all major sections to improve screen reader navigation.

-   **Design & Layout:**
    -   A fluid typography system using `clamp()` was implemented for smooth font scaling on all devices.
    -   The color palette was centralized in CSS variables, and text color contrast was improved to meet WCAG AA standards.
    -   The layout was refactored to use an `<img>` tag for the main product image instead of a CSS background, enabling better performance.
    -   A new responsive breakpoint was added for small mobile devices (`<480px`) to refine the mobile experience.

-   **Performance Optimization:**
    -   **Critical CSS:** Critical rendering path CSS for the hero section was inlined in the `<head>` to enable the fastest possible first paint.
    -   **Deferred Loading:** The main stylesheet and JavaScript file are now loaded asynchronously (`defer` and `media="print"`) to avoid render-blocking.
    -   **Font Optimization:** Google Fonts are now preloaded for faster discovery and rendering.
    -   **Image Attributes:** All images now include `loading="lazy"` and `decoding="async"` to defer offscreen image loading. The LCP element (hero video) is prioritized with `fetchpriority="high"`.

## 2. Lighthouse Performance

It is recommended to run a Lighthouse audit to quantify the improvements. The following table can be used to track the results.

| Metric (Mobile)       | Before | After (Expected) |
| --------------------- | :----: | :--------------: |
| **Performance**       |  TBD   |      **>85**     |
| First Contentful Paint|  TBD   |       <2.0s      |
| Largest Contentful Paint| TBD  |      **<2.5s**     |
| Cumulative Layout Shift |  TBD   |     **<0.05**    |
| **Accessibility**     |  TBD   |      **>90**     |

*Due to the inlining of critical CSS and deferred loading, a significant improvement in FCP and LCP is expected. The addition of ARIA labels and a correct heading structure should substantially increase the Accessibility score.*

## 3. Asset Sizes

The largest assets in the project are the background videos. Further optimization is possible by compressing these files.

| Asset                       | Size (approx) | Notes                               |
| --------------------------- | :-----------: | ----------------------------------- |
| `assets/images/section1.mp4`|      TBD      | Candidate for video compression (e.g., HandBrake). |
| `assets/images/section3.mp4`|      TBD      | Candidate for video compression.    |
| `assets/images/section4.jpg` |      TBD      | Candidate for WebP/AVIF conversion. |

*I am unable to check file sizes in this environment, but they should be manually checked and optimized.*

## 4. Future Recommendations

1.  **Image Format Conversion:** Convert `section4.jpg` to modern formats like WebP or AVIF using a `<picture>` element to serve smaller files to compatible browsers.
2.  **Video Compression:** The `.mp4` video files are large and significantly impact load time. They should be compressed using a tool like HandBrake to reduce their file size without a major loss in quality.
3.  **Implement a Favicon:** Create and link a `favicon.ico` and other relevant icons (`apple-touch-icon.png`, etc.) in the `<head>` to improve brand presence in browser tabs and saved links.
4.  **Add a Footer Navigation:** The footer is currently minimal. Consider adding links to key sections of the page (e.g., "Philosophy," "Essence") or a "Back to Top" link for better usability on a long-scrolling page.
5.  **Schema.org Markup:** Add JSON-LD schema markup (e.g., for `Product` or `Brand`) in the `<head>` to provide rich context for search engines, which can improve search result appearance.
