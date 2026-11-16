# Library form design system

Built surface: Operate, local librarian catalog entry. Light surface for a lit library desk; navy top navigation, teal primary action. No external fonts or decorative image assets.

Tokens: ink #172d43, muted #4e6171, line #d2dce2, paper #fff, ground #f1f5f7, action #08695f, focus #bb4f04. Segoe UI/Arial fallback; heading 34px desktop and 29px phone, section heading 21px, body 16px, labels 14px. Form padding 26px; input padding 11px 12px; button min-height 46px. Form boundary radius 12px, controls 6px.

Composition: 360px intake column beside flexible catalog; <=720px one column. Catalog scrolls within its own table container. Fine calculation follows below, separate heading and real form. Native form validation, server validation with input retention, status/alert roles, semantic labels/caption, keyboard focus and skip link. No animated content; pressed buttons respect reduced motion.

Verification: actual Chrome headless captures desktop 1440x1000 and narrow 390x1200 generated under docs/evidence. This session model cannot accept image inputs, so screenshots were captured but not visually certified. Mechanical detector found one wrapper border/padding warning; removed redundant table wrapper border (table cells retain rules). No claim of screen-reader certification. 32 executable backend/HTTP tests verify behavior.

Raster provenance: desktop.png and mobile.png are actual browser screenshots of this source, no generated imagery. No claims of human design approval or unseen visual review.
