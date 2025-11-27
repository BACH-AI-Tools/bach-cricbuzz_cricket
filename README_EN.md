# Cricbuzz Cricket MCP Server

English | [简体中文](./README.md) | [繁體中文](./README_ZH-TW.md)

## 🚀 Quick Start with EMCP Platform

**[EMCP](https://sit-emcp.kaleido.guru)** is a powerful MCP server management platform that allows you to quickly use various MCP servers without manual configuration!

### Quick Start:

1. 🌐 Visit **[EMCP Platform](https://sit-emcp.kaleido.guru)**
2. 📝 Register and login
3. 🎯 Go to **MCP Marketplace** to browse all available MCP servers
4. 🔍 Search or find this server (`bach-cricbuzz_cricket`)
5. 🎉 Click the **"Install MCP"** button
6. ✅ Done! You can now use it in your applications

### EMCP Platform Advantages:

- ✨ **Zero Configuration**: No need to manually edit config files
- 🎨 **Visual Management**: Easy-to-use GUI for managing all MCP servers
- 🔐 **Secure & Reliable**: Centralized API key and authentication management
- 🚀 **One-Click Install**: Rich selection of servers in MCP Marketplace
- 📊 **Usage Statistics**: Real-time service call monitoring

Visit **[EMCP Platform](https://sit-emcp.kaleido.guru)** now to start your MCP journey!


---

## Introduction

This is an MCP server for accessing the Cricbuzz Cricket API.

- **PyPI Package**: `bach-cricbuzz_cricket`
- **Version**: 1.0.0
- **Transport Protocol**: stdio


## 安装

### 从 PyPI 安装:

```bash
pip install bach-cricbuzz_cricket
```

### 从源码安装:

```bash
pip install -e .
```

## 运行

### 方式 1: 使用 uvx（推荐，无需安装）

```bash
# 运行（uvx 会自动安装并运行）
uvx --from bach-cricbuzz_cricket bach_cricbuzz_cricket

# 或指定版本
uvx --from bach-cricbuzz_cricket@latest bach_cricbuzz_cricket
```

### 方式 2: 直接运行（开发模式）

```bash
python server.py
```

### 方式 3: 安装后作为命令运行

```bash
# 安装
pip install bach-cricbuzz_cricket

# 运行（命令名使用下划线）
bach_cricbuzz_cricket
```

## Configuration

### API Authentication

This API requires authentication. Please set environment variable:

```bash
export API_KEY="your_api_key_here"
```

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `API_KEY` | API Key | Yes |
| `PORT` | N/A | No |
| `HOST` | N/A | No |



### 在 Claude Desktop 中使用

编辑 Claude Desktop 配置文件 `claude_desktop_config.json`:


```json
{
  "mcpServers": {
    "cricbuzz_cricket": {
      "command": "uvx",
      "args": ["--from", "bach-cricbuzz_cricket", "bach_cricbuzz_cricket"],
      "env": {
        "API_KEY": "your_api_key_here"
      }
    }
  }
}
```

**Note**: Replace `E:\path\to\cricbuzz_cricket\server.py` with the actual server file path.


## 可用工具

此服务器提供以下工具:


### `matchesget_scorecard_v2`

Get match scorecard

**端点**: `GET /mcenter/v1/{matchId}/hscard`


**参数**:

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.



---


### `matchesrecent`

List Recent Matches

**端点**: `GET /matches/v1/recent`



---


### `matcheslive`

GET Live Matches

**端点**: `GET /matches/v1/live`



---


### `matchesupcoming`

List Upcoming Matches

**端点**: `GET /matches/v1/upcoming`



---


### `matchesget_team`

Get players attended the match

**端点**: `GET /mcenter/v1/{matchId}/team/{teamId}`


**参数**:

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.

- `teamId` (string) *必需*: The value of teamId returned in …/matches/get-info endpoint



---


### `matchesget_info`

Get match info

**端点**: `GET /mcenter/v1/{matchId}`


**参数**:

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.



---


### `matcheslist`

List live, recent, upcoming matches

**端点**: `GET /matches/v1/{type}`


**参数**:

- `type` (string) *必需*: One of the followings : live|recent|upcoming



---


### `statsget_icc_rankings`

Get ICC rankings

**端点**: `GET /stats/v1/rankings/{category}`


**参数**:

- `formatType` (string) *必需*: One of the followings : test|odi|t20 (if isWomen parameter is 1, there will be no odi)

- `isWomen` (string): Set to 1 to get rankings for women

- `category` (string) *必需*: One of the followings : batsmen|bowlers|allrounders|teams



---


### `statsget_records`

Get records

**端点**: `GET /stats/v1/topstats/0`


**参数**:

- `statsType` (string) *必需*: The value of 'value' field returned in …/stats/get-record-filters endpoint

- `year` (string): Specify year to get records. Ex : 2021

- `matchType` (string): The value of matchTypeId field returned right in this endpoint

- `team` (string): The value of teamId field returned right in this endpoint

- `opponent` (string): The value of teamId field returned right in this endpoint



---


### `statsget_icc_standings`

Get ICC standings

**端点**: `GET /stats/v1/iccstanding/team/matchtype/{matchType}`


**参数**:

- `seasonId` (string): The value of seasonStandings/id field returned right in this endpoint

- `matchType` (string) *必需*: One of the followings : 1-World test championship|2-World cup super league



---


### `statsget_record_filters`

Get record filters

**端点**: `GET /stats/v1/topstats`



---


### `newslist_by_category`

List latest news by category

**端点**: `GET /news/v1/cat/{categoryId}`


**参数**:

- `categoryId` (string) *必需*: Filter news by category, the value of id field returned in …/news/get-categories



---


### `newslist_by_topic`

List latest news by topic

**端点**: `GET /news/v1/topics/{topicId}`


**参数**:

- `topicId` (string) *必需*: Filter news by topic, the value of id field returned in …/news/get-topics



---


### `playersget_career`

Get player career

**端点**: `GET /stats/v1/player/{playerId}/career`


**参数**:

- `playerId` (string) *必需*: The value of id field returned in …/players/list-trending, …/players/search endpoints



---


### `playersget_news`

Get news by player

**端点**: `GET /news/v1/player/{playerId}`


**参数**:

- `playerId` (string) *必需*: The value of id field returned in …/players/list-trending, …/players/search endpoints



---


### `venuesget_stats`

Get stats by venue

**端点**: `GET /stats/v1/venue/{venueId}`


**参数**:

- `venueId` (string) *必需*: The value of id field returned in …/series/get-venues endpoint



---


### `venuesget_info`

Get venue info

**端点**: `GET /venues/v1/{venueId}`


**参数**:

- `venueId` (string) *必需*: The value of id field returned in …/series/get-venues endpoint



---


### `teamsget_schedules`

Get scheduled matches for a team

**端点**: `GET /teams/v1/{teamId}/schedule`


**参数**:

- `teamId` (string) *必需*: The value of teamId field returned in …/teams/list endpoint



---


### `teamsget_players`

Get players by team

**端点**: `GET /teams/v1/{teamId}/players`


**参数**:

- `teamId` (string) *必需*: The value of teamId field returned in …/teams/list endpoint



---


### `teamsget_results`

Get matched results by team

**端点**: `GET /teams/v1/{teamId}/results`


**参数**:

- `teamId` (string) *必需*: The value of teamId field returned in …/teams/list endpoint



---


### `teamsget_stats_filters`

Get supported filters

**端点**: `GET /stats/v1/team/{teamId}`


**参数**:

- `teamId` (string) *必需*: The value of teamId field returned in …/teams/list endpoint



---


### `seriesget_matches`

Get recent and upcoming matches by series

**端点**: `GET /series/v1/{seriesId}`


**参数**:

- `seriesId` (string) *必需*: The value of id field returned in …/series/list or …/series/list-archives endpoints.



---


### `seriesget_squads`

Get squads by series

**端点**: `GET /series/v1/{seriesId}/squads`


**参数**:

- `seriesId` (string) *必需*: The value of id field returned in …/series/list or …/series/list-archives endpoints.



---


### `seriesget_points_table`

Get points table by series

**端点**: `GET /stats/v1/series/{seriesId}/points-table`


**参数**:

- `seriesId` (string) *必需*: The value of id field returned in …/series/list or …/series/list-archives endpoints.



---


### `seriesget_stats_filters`

Get supported filters

**端点**: `GET /stats/v1/series/{seriesId}`


**参数**:

- `seriesId` (string) *必需*: The value of id field returned in …/series/list or …/series/list-archives endpoints.



---


### `get_image`

This endpoint is used to get image by id

**端点**: `GET /img/v1/i1/{imageId}/i.jpg`


**参数**:

- `imageId` (string) *必需*: Add 'c' in the front of imageId



---


### `photosget_gallery`

Get photo gallery

**端点**: `GET /photos/v1/detail/{galleryId}`


**参数**:

- `galleryId` (string) *必需*: galleryId from photos/list service



---


### `photoslist`

List photo galleries

**端点**: `GET /photos/v1/index`



---


### `newsget_topics`

Get all available topics

**端点**: `GET /news/v1/topics`



---


### `newsget_categories`

Get all available categories

**端点**: `GET /news/v1/cat`



---


### `newsdetail`

Get news detail

**端点**: `GET /news/v1/detail/{newsId}`


**参数**:

- `newsId` (string) *必需*: The value of story/id field returned in …/news/list …/news/list-by-category …/news/list-by-topic endpoint



---


### `newslist`

List latest news

**端点**: `GET /news/v1/{type}`


**参数**:

- `type` (string) *必需*: One of the followings : index|premiumIndex



---


### `playersget_bowling`

Get player's bowling

**端点**: `GET /stats/v1/player/{playerId}/bowling`


**参数**:

- `playerId` (string) *必需*: The value of id field returned in …/players/list-trending, …/players/search endpoints



---


### `playersget_batting`

Get player's batting

**端点**: `GET /stats/v1/player/{playerId}/batting`


**参数**:

- `playerId` (string) *必需*: The value of id field returned in …/players/list-trending, …/players/search endpoints



---


### `playersget_info`

Get player info

**端点**: `GET /stats/v1/player/{playerId}`


**参数**:

- `playerId` (string) *必需*: The value of id field returned in …/players/list-trending, …/players/search endpoints



---


### `playerssearch`

Search player by name

**端点**: `GET /stats/v1/player/search`


**参数**:

- `plrN` (string) *必需*: Example value: Tucker



---


### `playerslist_trending`

List trending players

**端点**: `GET /stats/v1/player/trending`



---


### `venuesget_matches`

Get scheduled matches by venue

**端点**: `GET /venues/v1/{venueId}/matches`


**参数**:

- `venueId` (string) *必需*: The value of id field returned in …/series/get-venues endpoint



---


### `teamsget_news`

Get news by team

**端点**: `GET /news/v1/team/{teamId}`


**参数**:

- `teamId` (string) *必需*: The value of teamId field returned in …/teams/list endpoint



---


### `teamslist`

List teams

**端点**: `GET /teams/v1/{type}`


**参数**:

- `type` (string) *必需*: international|league|domestic|women



---


### `seriesget_venues`

Get venues by series

**端点**: `GET /series/v1/{seriesId}/venues`


**参数**:

- `seriesId` (string) *必需*: The value of id field returned in …/series/list or …/series/list-archives endpoints.



---


### `seriesget_players`

Get players by squad and series

**端点**: `GET /series/v1/{seriesId}/squads/{squadId}`


**参数**:

- `seriesId` (string) *必需*: The value of id field returned in …/series/list or …/series/list-archives endpoints.

- `squadId` (string) *必需*: The value of squadId field returned in …/series/get-squads endpoint



---


### `seriesget_news`

Get news by series

**端点**: `GET /news/v1/series/{seriesId}`


**参数**:

- `seriesId` (string) *必需*: The value of id field returned in …/series/list or …/series/list-archives endpoints.



---


### `serieslist_archives`

List archived series

**端点**: `GET /series/v1/archives/{type}`


**参数**:

- `year` (string): Example value: 

- `lastId` (string): For paging purpose, leave empty to load the first page, or the value of id field returned right in this endpoint.

- `type` (string) *必需*: One of the followings : international|league|domestic|women



---


### `serieslist`

List series

**端点**: `GET /series/v1/{type}`


**参数**:

- `type` (string) *必需*: One of the followings : international|league|domestic|women



---


### `matchesget_scorecard`

Get match scorecard

**端点**: `GET /mcenter/v1/{matchId}/scard`


**参数**:

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.



---


### `matchesget_leanback`

Get match leanback

**端点**: `GET /mcenter/v1/{matchId}/leanback`


**参数**:

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.



---


### `matchesget_commentaries`

Get match commentaries

**端点**: `GET /mcenter/v1/{matchId}/comm`


**参数**:

- `iid` (string): innings Id (Ex : 1)

- `tms` (string): For paging purpose, leave empty to load the first page, or an Epoch timestamp value in milliseconds (Ex : 1640883600000) to load the next page. You are interested in the 'timestamp' field returned right in this endpoint.

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.



---


### `matchesget_overs`

Get match overall

**端点**: `GET /mcenter/v1/{matchId}/overs`


**参数**:

- `iid` (string): innings Id (Ex : 1)

- `tms` (string): For paging purpose, leave empty to load the first page, or an Epoch timestamp value in milliseconds (Ex : 1640883600000) to load the next page. You are interested in the 'timestamp' field returned right in this endpoint.

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.



---


### `matchesget_commentaries_v2`

Get match commentaries

**端点**: `GET /mcenter/v1/{matchId}/hcomm`


**参数**:

- `iid` (string): innings Id (Ex : 1)

- `tms` (string): For paging purpose, leave empty to load the first page, or an Epoch timestamp value in milliseconds (Ex : 1640883600000) to load the next page. You are interested in the 'timestamp' field returned right in this endpoint.

- `matchId` (string) *必需*: The value of matchId field returned in …/matches/list, …/schedules/list, …/series/get-matches, …/teams/get-schedules, …/teams/get-results, …/venues/get-matches endpoints.



---


### `scheduleslist`

List scheduled matches

**端点**: `GET /schedule/v1/{type}`


**参数**:

- `lastTime` (string): For paging purpose, leave empty to load the first page, or an Epoch timestamp value in milliseconds (Ex : 1640883600000) to load the next page. You are interested in the 'startDt' field returned right in this endpoint.

- `type` (string) *必需*: One of the followings : international|league|domestic|women



---



## 技术栈

- **FastMCP**: 快速、Pythonic 的 MCP 服务器框架
- **传输协议**: stdio
- **HTTP 客户端**: httpx

## 开发

This server is automatically generated by [API-to-MCP](https://github.com/BACH-AI-Tools/api-to-mcp) tool.

Version: 1.0.0
