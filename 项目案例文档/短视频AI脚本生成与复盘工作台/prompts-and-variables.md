# 提示词与变量定义

## 工作流输入变量

| 变量名 | 类型 | 必填 | 说明 |
|---|---|---:|---|
| `account_info` | String | 是 | 账号定位、受众、业务和目标 |
| `video_transcript` | String | 否 | 视频逐字稿；缺失时必须标记未知 |
| `video_evidence` | String | 否 | 对画面、字幕、音乐和节奏的文字观察 |
| `confirmed_mechanisms` | Array | 否 | 用户确认后保留的可迁移机制 |
| `topic_direction` | Object | 是 | 已确认主题、核心观点和素材条件 |
| `video_type` | Enum | 是 | 知识口播/过程实录/产品展示/自由创作 |

## 内容解析 Agent 输出

```json
{
  "summary": "一句话结论",
  "evidence_completeness": "high|medium|low",
  "hook": [],
  "structure": [],
  "visual_audio_analysis": [],
  "mechanisms": [],
  "unknowns": [],
  "risks": [],
  "learning_candidates": []
}
```

## 脚本生成 Agent 输出

```json
{
  "core_idea": "一个核心观点",
  "hooks": [],
  "recommended_hook": "",
  "narration": [],
  "shot_list": [],
  "editing_instructions": [],
  "publishing_package": {
    "titles": [],
    "cover_text": "",
    "hashtags": []
  },
  "fact_check": [],
  "needs_confirmation": []
}
```

## 接线原则

不要把固定文本“账号建档”作为素材导入节点的输入。原型阶段应将：

```text
开始.account_info
开始.video_transcript
开始.video_evidence
```

通过用户提示词传入素材导入节点，再输出结构化素材包。没有真实图片或视频文件时，视觉理解输入保持为空。

完整脱敏提示词见 [项目设计](project-design.md) 第 4 章。
