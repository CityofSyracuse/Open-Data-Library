# Open-Data-Library

## Syracuse Open Data Inventory Search

This project is a dataset explorer for the City of Syracuse Open Data portal.It pulls live dataset metadata from ArcGIS and displays it in a searchable, filterable, sortable table.

**Live site:**

[https://open-data-inventory-search.netlify.app/](https://open-data-inventory-search.netlify.app/)

---

## What This Is For

This tool gives staff and the public a clean way to:

- Search datasets by title
- Filter by Open Data category
- Filter by publish year
- Sort by title, publish date, or updated date
- Quickly see how many datasets exist and how many match filters

---

## Data & Filtering

We pull from the city ArcGIS group:

<pre class="overflow-visible! px-0!" data-start="1106" data-end="1146"><div class="contain-inline-size rounded-2xl corner-superellipse/1.1 relative bg-token-sidebar-surface-primary"><div class="sticky top-[calc(var(--sticky-padding-top)+9*var(--spacing))]"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>af5799e7f6d84c5a944b053a47e18121</span><span>
</span></span></code></div></div></pre>

Using the ArcGIS REST Search API. The script paginates automatically until all datasets in the group are retrieved.

Categories come from:

<pre class="overflow-visible! px-0!" data-start="1711" data-end="1739"><div class="contain-inline-size rounded-2xl corner-superellipse/1.1 relative bg-token-sidebar-surface-primary"><div class="sticky top-[calc(var(--sticky-padding-top)+9*var(--spacing))]"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>item.groupCategories
</span></span></code></div></div></pre>

ArcGIS stores these like:

<pre class="overflow-visible! px-0!" data-start="1768" data-end="1802"><div class="contain-inline-size rounded-2xl corner-superellipse/1.1 relative bg-token-sidebar-surface-primary"><div class="sticky top-[calc(var(--sticky-padding-top)+9*var(--spacing))]"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>/Categories/</span><span>Infrastructure</span><span>
</span></span></code></div></div></pre>

We strip `/Categories/` and display the clean category name.

If categories change in ArcGIS, the dropdown updates automatically

---

### Year Filter

Year is based on **Date Published (`created`)**

---

## How to Run Locally

1. Clone the repository:

<pre class="overflow-visible! px-0!" data-start="2511" data-end="2578"><div class="contain-inline-size rounded-2xl corner-superellipse/1.1 relative bg-token-sidebar-surface-primary"><div class="sticky top-[calc(var(--sticky-padding-top)+9*var(--spacing))]"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>git </span><span>clone</span><span> https://github.com/YOUR_ORG/Open-Data-Library.git
</span></span></code></div></div></pre>

2. Move into the folder:

<pre class="overflow-visible! px-0!" data-start="2606" data-end="2634"><div class="contain-inline-size rounded-2xl corner-superellipse/1.1 relative bg-token-sidebar-surface-primary"><div class="sticky top-[calc(var(--sticky-padding-top)+9*var(--spacing))]"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>cd</span><span></span><span>Open-Data</span><span>-Library</span><span>
</span></span></code></div></div></pre>

3. Open `index.html` in your browser. or use Live Server in VS Code.

---

## Deployment

The site is deployed through Netlify.

- The `main` branch is connected to Netlify.
- Any merge into `main` triggers an automatic deploy.

If something looks wrong after a merge:

- Check Netlify deploy logs
- Hard refresh the browser

---

## Making Changes

If you’re modifying functionality, always use a branch.

### Create a branch:

<pre class="overflow-visible! px-0!" data-start="3173" data-end="3220"><div class="contain-inline-size rounded-2xl corner-superellipse/1.1 relative bg-token-sidebar-surface-primary"><div class="sticky top-[calc(var(--sticky-padding-top)+9*var(--spacing))]"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>git checkout -b feature/describe-change
</span></span></code></div></div></pre>

Make your edits to `index.html`.

Test locally:

- Confirm filters stack properly
- Confirm sorting still works
- Check browser console for errors

Then commit:

<pre class="overflow-visible! px-0!" data-start="3383" data-end="3484"><div class="contain-inline-size rounded-2xl corner-superellipse/1.1 relative bg-token-sidebar-surface-primary"><div class="sticky top-[calc(var(--sticky-padding-top)+9*var(--spacing))]"><div class="absolute end-0 bottom-0 flex h-9 items-center pe-2"><div class="bg-token-bg-elevated-secondary text-token-text-secondary flex items-center gap-4 rounded-sm px-2 font-sans text-xs"></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="whitespace-pre!"><span><span>git </span><span>add</span><span> .
git </span><span>commit</span><span></span><span>-</span><span>m "Clear description of change"
git push origin feature</span><span>/</span><span>describe</span><span>-</span><span>change
</span></span></code></div></div></pre>

Open a Pull Request for review.

---
