# Shopify Hierarchical Breadcrumbs

Enhanced breadcrumbs for Shopify Sleek theme with multi-level collection hierarchy and JSON-LD schema.

## Features
- ✅ Multi-level collection hierarchy (Home > Parent > Child > Product)
- ✅ JSON-LD BreadcrumbList schema for SEO
- ✅ Multi-language support via Shopify translations
- ✅ Fallback to "All Products" if no metafields set
- ✅ **Mobile horizontal scroll** with optimized UX
- ✅ Preserves Sleek theme styling

## Required Metafields

## Setup Instructions

### Step 1: Create Product Metafield
1. Go to **Shopify Admin → Settings → Metafields and metaobjects → Products**
2. Click **Add definition**
3. Set:
   - Name: Breadcrumbs
   - Namespace/Key: `breadcrumb.primary_collection`
   - Type: **List of Collections**
4. Save

### Step 2: Install Code
1. Copy `sections/breadcrumbs.liquid` from this repo
2. Replace your existing `sections/breadcrumbs.liquid` in Shopify theme editor
3. Save

### Step 3: Add Mobile Scroll CSS
**⚠️ IMPORTANT:** For mobile devices, breadcrumbs need horizontal scroll to prevent wrapping.

1. Go to **Shopify Admin → Online Store → Themes → Actions → Edit code**
2. Open **`assets/theme.css`**
3. **Scroll to the very end** of the file (after the last `}`)
4. **Paste the code:** `assets/theme.css` in Shopify theme editor
5. Save

### Step 4: Configure Hierarchy
Example: Product "Red Gel Polish" should show: Home > Nail Products > Gel Polish > Red Gel Polish

1. **On the product** ("Red Gel Polish"):
   - Set `breadcrumb.primary_collection` = "Gel Polish" (leaf collection)

## Testing

1. View a product page
2. Check breadcrumbs display correctly
3. Validate JSON-LD: https://search.google.com/test/rich-results

## Translation Keys

Make sure these exist in your locale files:

**Romanian (`locales/ro.json`):**
```json
{
  "general": {
    "breadcrumbs": {
      "home": "Acasă",
      "collections": "Toate Produsele"
    }
  }
}
```

**English (`locales/en.default.json`):**
```json
{
  "general": {
    "breadcrumbs": {
      "home": "Home",
      "collections": "All Products"
    }
  }
}
```

## Example Output

**HTML:**
```
Home > Nail Products > Gel Polish > Red Gel Polish
```

**JSON-LD:**
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [...]
}
```

## Compatibility
- **Theme**: Sleek by FoxEcom
- **Shopify**: All plans
- **Multi-language**: Yes (via Shopify Markets)
- **Mobile**: Tested on iPhone SE, iPhone 12, Galaxy S8, Pixel 5


## License
MIT License - Free to use and modify

## Alina E Popa
Created: January 2026
