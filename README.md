# Shopify Hierarchical Breadcrumbs

Enhanced breadcrumbs for Shopify Sleek theme with multi-level collection hierarchy and JSON-LD schema.

## Features
- ✅ Multi-level collection hierarchy (Home > Parent > Child > Product)
- ✅ JSON-LD BreadcrumbList schema for SEO
- ✅ Multi-language support via Shopify translations
- ✅ Fallback to "All Products" if no metafields set
- ✅ Preserves Sleek theme styling

## Required Metafields

### 1. Product Metafield (already exists in Sleek)
- **Namespace/Key**: `breadcrumb.primary_collection`
- **Type**: Collection (single)
- **Purpose**: Stores the leaf collection

### 2. Collection Metafield (NEW - create this)
- **Namespace/Key**: `breadcrumbs.collections`
- **Type**: List of Collections
- **Purpose**: Stores parent collections in order

## Setup Instructions

### Step 1: Create Collection Metafield
1. Go to **Shopify Admin → Settings → Custom Data → Collections**
2. Click **Add definition**
3. Set:
   - Name: Parent Collections
   - Namespace/Key: `breadcrumbs.collections`
   - Type: **List of Collections**
4. Save

### Step 2: Install Code
1. Copy `sections/breadcrumbs.liquid` from this repo
2. Replace your existing `sections/breadcrumbs.liquid` in Shopify theme editor

### Step 3: Configure Hierarchy
Example: Product "Red Gel Polish" should show: Home > Nail Products > Gel Polish > Red Gel Polish

1. **On the product** ("Red Gel Polish"):
   - Set `breadcrumb.primary_collection` = "Gel Polish" (leaf collection)

2. **On the leaf collection** ("Gel Polish"):
   - Set `breadcrumbs.collections` = ["Nail Products"] (parent list)

3. **On parent collection** ("Nail Products"):
   - Leave `breadcrumbs.collections` empty (it's top-level)

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

## License
MIT License - Free to use and modify

## Alina E Popa
Created: January 2026
