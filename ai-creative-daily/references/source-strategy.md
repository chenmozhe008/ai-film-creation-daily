# Source Strategy

Use current Codex web research. Do not depend on old OpenClaw scripts or GLM tasks.

## Baseline Search Pass

Run searches in these buckets:

- Official AI providers: OpenAI, Anthropic, Google DeepMind/Gemini, Meta AI, Microsoft, Adobe, Figma, Canva, AWS, Nvidia, Qwen, Kuaishou/Kling, ByteDance/Seedance, Midjourney, Black Forest Labs.
- Creative tools: Runway, Luma, Pika, Kling/可灵, 即梦, HeyGen, ElevenLabs, Suno, Udio, Descript, CapCut, Premiere, Photoshop, Blender, Ableton, Resolve.
- Developer/agent tools only when creator workflow relevant: Codex, Claude Code, Cursor, OpenClaw, MCP, workflow automation, browser agents.
- Chinese creator ecosystem: B站 AI生成/可灵/即梦/AI短剧/AI绘画/角色一致性/分镜/运镜/AI剪辑/AI配音; 微信公众号; 小红书 creative workflow posts.

The collection must run three independent lanes. Do not let official AI news crowd out creator-native material.

1. **X account-pool lane**: read `references/x-lists.json`, sample from every list, and search account-specific posts before generic news searches.
2. **Chinese creator-platform lane**: run B站, 小红书, 微信公众号 discovery for tutorials and works/cases.
3. **Official/platform lane**: run official AI provider and product release searches.

If lanes 1 or 2 produce no final item, the run review must say whether this was due to access limits, date/traction verification failure, or genuinely weak results.

Prefer query forms with date anchors:

```text
{entity} announcement {month day year}
{entity} AI video update {month year}
{entity} creative workflow {month year}
AI生成 视频 教程 {YYYY年M月D日}
可灵 即梦 AI短剧 案例 {YYYY年M月D日}
site:bilibili.com AI生成 视频 {YYYY年M月D日}
site:youtube.com AI generated short film {month year}
```

## Section 3: Tutorials And Methods

Only include items that teach a reproducible creative operation:

- Prompting with camera movement, shot type, timing, character consistency, storyboard, edit rhythm.
- Image/video workflow breakdowns: Midjourney/Flux/Runway/Kling/即梦/Seedance/Sora/Veo.
- Design workflow: Figma/Canva/Adobe/Claude creative connectors when it changes UI, layout, asset production, or brand system work.
- Audio/music workflow: voice clone, sound design, music generation, sync to video.
- Agent workflow: only if it automates a creative production task, not generic coding.

Reject:

- Pure industry commentary.
- News rewritten as “教程”.
- Tool lists without concrete steps.
- Security incidents unless they directly change creator workflow.

Mandatory tutorial discovery pass:

```text
site:bilibili.com AI视频 工作流 可灵 即梦 角色一致性
site:bilibili.com AI短剧 教程 分镜 运镜
site:bilibili.com Midjourney Runway Kling 工作流
site:xiaohongshu.com AI短剧 工作流 可灵 即梦
site:xiaohongshu.com AI绘画 角色一致性 工作流
site:mp.weixin.qq.com AI短剧 工作流 可灵 即梦
site:mp.weixin.qq.com AI视频 角色一致性 分镜
```

For Section 3, prefer creator posts that contain steps, screenshots, prompts, node graphs, before/after comparisons, or production notes. A product announcement can only enter Section 3 if it contains an actual repeatable workflow.

## Section 4: Works And Cases

Need a concrete work, creator project, or production deployment. It must have an independent link and at least one traction signal:

- B站: ideally 10万+ views, or lower only if the work is unusually relevant and the report states why.
- YouTube: 5,000+ views or clear creator/community discussion.
- X/Reddit: 20+ likes/upvotes or meaningful discussion.
- Professional case: studio, brand, creator team, or toolmaker publishes a production breakdown.

Search actively every day. Do not let this section go empty just because official news was abundant.

Recommended search passes:

```text
AI generated short film viral {month year}
AI video showcase Runway Kling Seedance {month year}
AI music video generated {month year}
AI animation case study {month year}
B站 AI短剧 可灵 即梦 {YYYY年M月D日}
B站 AI生成 角色一致性 视频 {YYYY年M月D日}
小红书 AI短剧 工作流 可灵 即梦
微信公众号 AI短剧 可灵 即梦 工作流
```

If you cannot verify date or traction, put it in notes, not the report.

Mandatory case discovery pass:

```text
site:bilibili.com AI短剧 可灵 即梦 播放
site:bilibili.com AI生成 短片 可灵 即梦
site:bilibili.com AI音乐 MV AI生成
site:x.com AI short film Runway Kling Seedance
site:x.com AI video showcase Midjourney Runway Kling
site:youtube.com AI generated short film Runway Kling
site:xiaohongshu.com AI短剧 作品 可灵 即梦
```

Case acceptance rule:

- A tool integration demo is not a work/case unless it shows a concrete output, named creator/team, and a production lesson.
- A company announcement is not a case.
- A gallery homepage is not enough; find the independent work page or creator post.
- If using B站/小红书 and exact metrics are hard to read, open the item or use search snippets. If still unverified, keep it as candidate-notes only.

## X Account-Pool Lane

`references/x-lists.json` is a primary source map, not a passive backup. Each daily run must sample:

- 12-20 creator/KOL accounts, with priority to `kol_creators` and `kol_chinese`.
- 8-12 creative video/image/music tool accounts.
- 8-12 official AI platform/tool accounts.
- 5-8 founders/researchers only if their posts affect creative tools or creator workflows.

Run order matters: creator/KOL and creative-tool accounts must be searched before official platform accounts. Official accounts are useful for Sections 1-2, but they must not consume the collection budget before Sections 3-4 have creator-native candidates.

Start this lane with the query-pack helper so the account order is deterministic and creator-first:

```bash
python3 ai-creative-daily/scripts/build_x_query_pack.py --date YYYY-MM-DD --format text
```

The first visible blocks must be `kol_creators` and `kol_chinese`. If the first blocks are official company accounts, stop and fix the account-pack order before collecting.

Use account-specific queries:

```text
site:x.com/{handle} "workflow" OR "tutorial" OR "breakdown" OR "prompt guide"
site:x.com/{handle} "behind the scenes" OR "case study" OR "making of"
site:x.com/{handle} "AI short film" OR "AI video" OR "made with" OR "showcase"
site:x.com/{handle} "Runway" OR "Kling" OR "Seedance" OR "Midjourney" OR "Veo" OR "Sora"
site:x.com/{handle} "camera" OR "shot" OR "storyboard" OR "character consistency"
{handle} AI creative workflow {month day year}
{handle} AI video prompt camera workflow {month year}
{handle} AI generated video case study showcase {month year}
```

Before writing the final report, X must have produced at least:

- 5 creator/KOL tutorial or workflow candidates for Section 3 review.
- 3 creator/tool showcase or work/case candidates for Section 4 review.
- 2 Chinese creator candidates from `kol_chinese`, or a written blocker explaining why none could be verified.

If these are missing, do not proceed directly to official news. Run the second X pass below, then rerun B站/小红书/公众号 searches using the strongest handles/tools discovered from X.

When search results expose a valuable X post but direct X access is blocked, search the exact post text, handle, or URL through web search and secondary mirrors. Do not discard it just because X itself is hard to fetch.

Important: X account-pool results are often high-value but stale. Treat account-pool search as discovery first, then validate date before final inclusion.

- If a result is older than the daily window but contains a strong reusable workflow, save it as method-library context only; do not include it as today's item.
- For today's report, combine handle + date + creative intent. Example: `site:x.com/chatcutapp Seedance prompt guide April 2026` found a useful Seedance prompt workflow, but it still needs window validation.
- For creator/KOL accounts, search their handle with these intent terms: `workflow`, `prompt guide`, `behind the scenes`, `case study`, `made with`, `AI short film`, `breakdown`, `tutorial`, `prompt`, `shot`, `camera`, `character consistency`.
- Prefer posts that include screenshots, videos, prompt structure, reference-asset rules, or production constraints.

If Section 3 or Section 4 has no viable candidates after the first pass, run a second X pass before writing:

```text
site:x.com/{creator_handle} "made with" "Kling" OR "Runway" OR "Seedance"
site:x.com/{creator_handle} "prompt" "camera" "AI video"
site:x.com/{tool_handle} "showcase" OR "community" OR "creator"
site:x.com/{tool_handle} "workflow" OR "tutorial" OR "behind the scenes"
```

## Chinese Platform Notes

- B站 search/snippets often hide exact date and view count. Use browser/search result pages, creator page, or secondary references to confirm.
- 小红书 search is noisy. Treat it as discovery; verify with the actual post if login is available.
- 微信公众号 content often appears via Sogou or mirrored pages. Prefer original mp.weixin.qq.com when accessible.
- If login state is unavailable, tell the user exactly which platform login would improve results.

Chinese creator-platform lane must target creator intent, not generic news:

- B站: prioritize `AI短剧`, `AI视频`, `可灵`, `即梦`, `Seedance`, `角色一致性`, `分镜`, `运镜`, `AI音乐MV`, `AI动画`, `工作流`.
- 小红书: prioritize practical notes and creator breakdowns; do not trust listicles unless the original post shows a workflow.
- 微信公众号: prioritize long-form workflow posts and production breakdowns; reject pure reposted news.

Freshness handling for Chinese platforms:

- Search results frequently surface old but useful B站 courses. These are valuable for source discovery but fail the daily freshness gate.
- Daily inclusion needs one of: publish date inside the window, clear same-day update, or same-day resurfacing by a credible creator with a new insight.
- Old evergreen tutorials can inform the method rubric and keywords, but should not appear as a daily news item.
- For today's candidate pool, record old-but-useful tutorials separately as `method-library`, not final candidates.

## Source Ranking

1. Official announcement or product docs.
2. Primary creator/studio/toolmaker post.
3. Reputable tech/creative media with date and named source.
4. Aggregators only as discovery, not final evidence unless clearly dated and linked.

Avoid overusing generic AI news aggregators. They are useful for leads, but the final report should cite primary or high-quality secondary sources.
