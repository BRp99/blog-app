# Blog Application

This is a blog application built with **Next.js**, **TypeScript**, and **Tailwind CSS**. The app fetches blog posts from the [JSONPlaceholder API](https://jsonplaceholder.typicode.com/posts) and displays them in a responsive layout. In the end I make blog application compatible with IPFS. 

## Features

### Homepage (/)

- Fetches a list of blog posts using `getStaticProps`.
- Displays posts in a responsive grid layout.
- Each post card includes:
  - Title (clickable link to post details page)
  - First 100 characters of the body
  - "Read More" link to post details page
  - Tags for filtering posts

### Post Details page (/post/[id])

- Dynamic route for each post.
- Uses `getStaticPaths` and `getStaticProps` to generate pages.
- Displays full post details including title, body, post ID, and author ID.

### About page (/about)

- Placeholder page for additional information about the blog.

## Tech stack

- Next.js;
- TypeScript;
- Tailwind CSS;
- JSONPlaceholder API

## Project setup

1. Clone the repository: `https://github.com/BRp99/blog-app.git`
2. Navigate to the project directory: `cd blog-app`
3. Install dependencies:
   `npm install`

4. Run the development server:
   `npm run dev`

## Approach and Advanced Features

### Approach

The application is built using Next.js framework for static site generation (SSG). TypeScript is used for type safety, and Tailwind CSS is used for styling. The JSONPlaceholder API is used to fetch blog post data.

### Advanced features

SSG: The homepage and post details pages are statically generated using getStaticProps and getStaticPaths;

Responsive Design: The application is designed to be fully responsive using Tailwind CSS;

Reusable Components: Component Layout are used to ensure consistent styling and structure across the application;

Utility Functions: `generatePostTags` are used to process and display data.

#### Changes for IPFS Deployment:

To make the blog application compatible with IPFS, I made the following modifications to the next.config.ts file:

```
const nextConfig: NextConfig = {
  output: "export", // Export as a static site
  distDir: "out", // Ensure generated files are saved in the "out" folder - important for IPFS
  images: {
    unoptimized: true, // Next.js normally optimizes images dynamically - this does not work on IPFS
  },
  reactStrictMode: true,
};

```

- To deploy on IPFS Desktop I run `npm run build` and distDir: "out" ensures that the exported files are stored in the out/ directory;
- The content of the out/ directory can be uploaded to IPFS;
- I import the folder `out` in IPFS Desktop and I Pin the content that is inside the folder `out`;
- After Pinning the content I get the CID (Content Identifier), which is a unique string generated by IPFS to identify the content: https://ipfs.io/ipfs/[CID]

- This is the URL for LOCAL gateway:
  `https://ipfs.io/ipns/k51qzi5uqu5dl6v3fqwfql562786nhzl5lrdsnixg4qarfu0a176ry936foj0q`

![localhost-url](https://github.com/user-attachments/assets/9a0aab30-c5a5-4c86-852d-035b042ad84f)


### Additional information

- Custom \_app.tsx for global layout;
- Custom \_document.tsx for document structure;
- Global CSS file for Tailwind CSS configuration;
- Type definitions in `types.ts`;
- Utility functions in `generatePostTags.ts`;
- `Layout` component for wrapping sections with consistent styling.
- Project deployed on Vercel.

You can acess the live version of this project here: https://blog-app-brp99s-projects.vercel.app/
