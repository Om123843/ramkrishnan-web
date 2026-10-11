# Ramkrishna Veg Resto & Banquet landing pages

These are standalone HTML pages with inline CSS and JavaScript:

- `index.html` — main restaurant and banquet landing page.
- `restaurant.html` — restaurant-search landing page.
- `banquet.html` — banquet-search landing page and enquiry form.

## Before publishing

The user supplied this address: `Hissa 1B2, Serial 14, Maheshwari Hospitality, BRT Road, Ravet, Pune 412101`, phone `+917517525435`, and approximate coordinates `18.65089, 73.73923`. These are populated across the pages and structured data. Confirm the address and phone against the Google Business Profile before launch. Another deck reportedly lists the phone as `075175 25436`, so verify the differing number; the pages use the number explicitly supplied here. Opening hours remain marked unconfirmed: the deck lists 8 am–4 pm and 7–11 pm, while Zomato and Justdial reportedly list an 11 am opening. No opening hours are asserted in JSON-LD.

Other business-specific details that were not supplied are visibly marked as placeholders. Replace every remaining placeholder consistently across the pages, JSON-LD and sitemap. In each page's inline `SITE` settings:

- `phone`: currently prefilled with the user-supplied `+917517525435`. Phone buttons and visible phone numbers link to `tel:+917517525435`.
- `mapUrl`: currently opens Google Maps at the supplied approximate coordinates. Confirm the pin before using it as the final directions destination.
- `mapEmbedUrl`: currently embeds the supplied approximate coordinates in a lazy-loaded map iframe. Confirm the pin; replace with a verified embed URL if needed.
- `whatsappNumber`: verified WhatsApp number in international format, digits only. Used on `banquet.html`.
- `menuUrl`: currently points to the supplied PDF at `menu/Ramkrishna_Restaurant_Menu.pdf`.
- `reviewsUrl`: verified Google review link.
- `formEndpoint`: working HTTPS URL such as `[Formspree / Google Forms / Google Apps Script URL]` that accepts POST requests and supports browser CORS. Until set, the form reports that it is not connected and will not claim a submission succeeded.
- `gaId`: actual GA4 measurement ID in the form `[G-XXXXXXXXXX]`. Analytics is not loaded while this is unset or a placeholder.

Ravet is used in the headlines and SEO copy, based on the supplied address. Replace the canonical and Open Graph URLs with the final page URLs. Update `sitemap.xml` and `robots.txt` with the production domain. The user-provided images are optimized as `images/gallery-01.jpg` through `images/gallery-11.jpg`; the full set appears in the main gallery, menu booklet images appear on `restaurant.html`, and venue/package views appear on `banquet.html`. `images/restaurant-exterior.jpg` from the earlier attachment is also retained on the home and restaurant pages. Gallery images are lazy-loaded and have descriptive alt text. Menu/package captions ask users to verify their printed details before treating them as current. Other image placeholders may be replaced only with approved photos; provide descriptive `alt` text on every replacement `<img>`.

The form validates the required name and 10-digit phone number. It also sends the three UTM values and a `lead_qualification` value (`qualified` when date, expected guests and event type are all provided).

## GA4 events and Google Ads

After configuring `gaId`, verify the following events in GA4 DebugView or Realtime: `click_to_call`, `get_directions`, `whatsapp_click`, `menu_view` and `banquet_enquiry_submit`. Each event includes `page_type` and the `utm_source`, `utm_medium` and `utm_campaign` values read from the landing-page URL. The successful enquiry event is emitted only after the endpoint responds successfully.

1. In GA4, go to **Admin → Events** and wait until each event has been received. Mark the events you want to optimize for as **key events** (formerly conversions).
2. In Google Ads, link the Ads account to the GA4 property under **Admin → Product links → Google Ads links**.
3. In Google Ads, open **Goals → Conversions → Summary → New conversion action → Import → Google Analytics 4 properties (Web)**. Select the desired key events and import them.
4. Confirm conversion status and attribution after real traffic arrives. The Google Ads conversion-tag placeholder is included in each HTML file; install a direct Ads tag only if it is part of the approved measurement setup, and avoid duplicate counting with imported GA4 conversions.

## QA notes before launch

- Responsive rules target narrow phones (including 360px) and tablet/desktop widths. Check the actual deployed pages at 360px and 768px after adding verified data.
- The supplied address, phone and user-provided venue/menu images are displayed; the disputed opening hours remain visibly unconfirmed. Menu and package details shown in the booklet images are not independently verified. No additional menu claims, venue capacity/facilities, reviews or offers have been invented.
- The phone link is wired to the supplied number. The Google Maps directions link uses the supplied approximate coordinates; confirm the pin. Menu, WhatsApp, form delivery and external analytics still need their verified values/endpoints.
- The pages use system fonts and compressed user-provided images; no stock images, framework, or blocking third-party script is required. GA4's script is async and loads only after a real measurement ID is configured.
