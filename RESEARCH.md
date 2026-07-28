# Research Log: 3D Reconstruction Methods for Heritage Sites Without LiDAR Access

## Research Question
What are the best 3D reconstruction methods for heritage sites with limited or no LiDAR access, and how does COLMAP compare to alternatives?

## Source Log

| # | Title | Link | Date | Credibility | Summary |
|---|-------|------|------|-------------|---------|
| 1 | COLMAP official docs & tutorial | https://colmap.github.io/ | Ongoing | Official project docs, primary source | COLMAP is described by its own creators as a general-purpose Structure-from-Motion/Multi-View Stereo pipeline that reconstructs 3D structure and camera positions from overlapping 2D images. Confirms I used the tool as intended for the Mohenjo-daro reconstruction — an image-only pipeline, no LiDAR needed. |
| 2 | COLMAP GitHub repo & releases | https://github.com/colmap/colmap | Actively maintained | Primary source, open-source codebase | Shows COLMAP is actively developed, with recent additions like fallback image registration for images without full 3-view overlap. Relevant because my dataset (Google Images photos, not controlled capture) is exactly the messy input this fallback is meant to handle. |
| 3 | Photogrammetry Software: A Comparative Review of COLMAP and Meshroom (Springer, 2026) | https://link.springer.com/chapter/10.1007/978-3-032-13056-3_38 | 2026 | Peer-reviewed academic paper | Frames the core problem directly: 3D scans historically required LiDAR and 360° cameras, but photogrammetry software now builds 3D models from ordinary 2D images instead. Justifies why my no-LiDAR, photo-only approach is a legitimate method, not a workaround. |
| 4 | Nemeh Rihani, Digital technologies for reconstruction using crowdsourced images (2023) | https://journals.sagepub.com/doi/full/10.1177/14780771231168224 | 2023 | Peer-reviewed case study | Closest match to what I did: researchers rebuilt the destroyed Temple of Bel in Palmyra using only public visitor photos from social media and web search engines — no controlled capture, no LiDAR. Validates my Google Images fallback as a recognized research method. |
| 5 | Crowdsource and web-published images for 3D heritage documentation (ScienceDirect) | https://www.sciencedirect.com/science/article/abs/pii/S1296207416300371 | 2016 | Peer-reviewed journal article | Explains why crowdsourced/web images are attractive for non-professionals: getting correct image overlap and camera orientation is hard, so researchers turned to abundant web image data instead, using volume and redundancy to compensate for inconsistent capture. |

## Write-up: Choosing a 3D Reconstruction Method for Heritage Sites With No LiDAR Access

When I built the COLMAP pipeline for Mohenjo-daro's Great Bath (Module 11), I hit a wall early: Wikimedia Commons, my planned image source, was blocked by my ISP. I had to fall back to Google Images photos instead — and at the time it felt like a compromise. Digging into the research afterward, it turns out this fallback is a documented, legitimate method in heritage photogrammetry, not a shortcut.

COLMAP itself is built exactly for this kind of problem: it's a Structure-from-Motion and Multi-View Stereo pipeline designed to reconstruct 3D geometry and camera positions purely from overlapping 2D photos, with no LiDAR or specialized capture equipment required.

More importantly, this isn't a novel workaround — it's an established research approach. Researchers rebuilt Palmyra's Temple of Bel, destroyed in 2015, using nothing but public visitor photos pulled from social media and web search engines. If a fully destroyed UNESCO heritage site can be reconstructed from scraped web images, then a Google Images fallback for an accessible site like Mohenjo-daro is well within reason.

The tradeoff is real, though: crowdsourced or web images lack the consistent overlap and camera orientation of a controlled capture, which is exactly why researchers have studied using web-sourced photos for heritage documentation specifically, treating image volume and redundancy as compensation for inconsistent capture conditions.

On the tool side, COLMAP compares favorably to alternatives like Meshroom for this kind of work: comparative reviews mark COLMAP as producing high-detail reconstructions with minimal smoothing, though it's less plug-and-play than Meshroom's drag-and-drop workflow. For a one-off heritage reconstruction where output quality mattered more than setup speed, COLMAP was the right call.

**Takeaway:** the Google Images fallback wasn't a limitation I had to work around — it's a recognized method with real precedent in cultural heritage preservation, and COLMAP was the right tool to pair it with.
