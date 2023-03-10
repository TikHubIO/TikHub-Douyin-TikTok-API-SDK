<div align="center">
<h1><a href="https://pypi.org/project/tikhub">TikHub_API</a></h1>
<a href="https://github.com/TikHubIO/TikHub_API_PyPi/blob/main/README.en.md">English</a> | <a href="https://github.com/TikHubIO/TikHub_API_PyPi/blob/main/README.md">简体中文</a>
</div>
<h4>简介</h4>
<p><a href="https://tikhub.io">TikHub</a>是抖音与TikTok非官方的RESTful API平台。</p>
<p>我们提供的API只能获取公开数据，即任何人都可以通过浏览器及APP等访问抖音或TikTok以获取它们。</p>
<p>如果您有任何建议或者需求，请联系我们，更多的功能正在开发中，敬请期待！</p>
<hr>
<h4>鉴权</h4>
<p>接口文档中带有🔒的接口需要在请求头中携带Token才可调用。</p>
<p>调用这些接口会使用你账户中的剩余请求次数！</p>

```python
from tikhub.api import *

# 初始化（Initialization)
api = API(
email='EMAIL@EXAMPLE.COM',
password='PASSWORD',
proxy=None,
)
```

<hr>
<h4>购买</h4>
<p>Website(🚧ing): <a href="https://tikhub.io">https://tikhub.io</a></p>
<p>Discord(💳buy): <a href="https://discord.gg/KnWCrgCERq">https://discord.gg/KnWCrgCERq</a></p>
<p>Github: <a href="https://github.com/TikHubIO">https://github.com/TikHubIO</a></p>
<p>Email: <a href="mailto:tikhub.io@proton.me">tikhub.io@proton.me</a></p>
<p>WeChat/微信: Evil-Bot</p>
<hr>
<h4>公告</h4>
<p>TikHub的API将使用<strong>免费加付费</strong>的形式运行。</p>
<p>登录后，通过点击以下链接可以免费试用7天，包含2000次API请求，只限新用户。</p>
<a href="https://api.tikhub.io/promotion/claim?promotion_id=1">https://api.tikhub.io/promotion/claim?promotion_id=1</a>
<p>登录后，通过点击以下链接进行签到可以随机获得50-100次API请求，每24小时可签到一次。</p>
<a href="https://api.tikhub.io/promotion/daily_check_in">https://api.tikhub.io/promotion/daily_check_in</a>
<hr>

## 使用示例

> Check[test.py](https://github.com/TikHubIO/TikHub_PyPi/blob/main/test/test.py)

-   Install

```bash
pip install tikhub
```

-   Usage

```python
from tikhub.api import *


async def async_test() -> None:
    # 异步测试/Async test

    tiktok_url = 'https://www.tiktok.com/@evil0ctal/video/7156033831819037994'

    tiktok_music_url = 'https://www.tiktok.com/music/original-sound-7128362040359488261'

    douyin_url = 'https://www.douyin.com/video/7153585499477757192'

    douyin_user_url = 'https://www.douyin.com/user/MS4wLjABAAAAaNJuvXC83kL5nhaZHubKdjsRJQovgz58wXzlLnJUsslG-Kb24TM1QJlf_2HMaUJk'

    print("Test start...\n")
    start_time = time.time()

    # 获取TikHub请求头/Get TikHub request header
    r = await api.user_login()
    print("Running test : API.user_login()")
    print(r)

    # 获取TikHub用户信息/Get TikHub user information
    print("Running test : API.get_user_info()")
    r = await api.get_user_info()
    print(r)

    print("\nRunning ALL TikTok methods test...\n")

    # 获取单个视频数据/Get single video data
    print("Running test : API.get_tiktok_video_data()")
    r = await api.get_tiktok_video_data(tiktok_url)
    # print(r)

    # 获取获取用户主页的所有视频数据/Get all video data on the user's homepage
    print("Running test : API.get_tiktok_profile_videos()")
    r = await api.get_tiktok_profile_videos(tiktok_url, cursor=None, count=None, get_all=False)
    print(f'Get {len(r)} videos from profile')

    # 获取用户主页的所有点赞视频数据/Get all liked video data on the user's homepage
    print("Running test : API.get_tiktok_profile_liked_videos()")
    r = await api.get_tiktok_profile_liked_videos(tiktok_url, cursor=None, count=None, get_all=False)
    print(f'Get {len(r)} liked videos from profile')

    # 获取TikTok视频的所有评论数据/Get all comment data of TikTok video
    print("Running test : API.get_tiktok_video_comments()")
    r = await api.get_tiktok_video_comments(tiktok_url, cursor=None, count=None, get_all=False)
    print(f'Get {len(r)} comments from video')

    # 获取音乐页面上的所有(理论上能抓取到的)视频数据/Get all (theoretically) video data on the music page
    print("Running test : API.get_tiktok_music_videos()")
    r = await api.get_tiktok_music_videos(tiktok_music_url, cursor=None, count=None, get_all=False)
    print(f'Get {len(r)} videos from music')

    print("\nRunning ALL Douyin methods test...\n")

    # 获取单个视频数据/Get single video data
    print("Running test : API.get_douyin_video_data()")
    r = await api.get_douyin_video_data(douyin_url)

    # 获取获取用户主页的所有视频数据/Get all video data on the user's homepage
    print("Running test : API.get_douyin_profile_videos()")
    r = await api.get_douyin_profile_videos(douyin_user_url, cursor=None, count=None, get_all=False)
    print(f'Get {len(r)} videos from profile')

    # 获取用户主页的所有点赞视频数据/Get all liked video data on the user's homepage
    print("Running test : API.get_douyin_profile_liked_videos()")
    r = await api.get_douyin_profile_liked_videos(douyin_user_url, cursor=None, count=None, get_all=False)
    print(f'Get {len(r)} liked videos from profile')

    # 获取抖音视频的所有评论数据/Get all comment data of Douyin video
    print("Running test : API.get_douyin_video_comments()")
    r = await api.get_douyin_video_comments(douyin_url, cursor=None, count=None, get_all=False)
    print(f'Get {len(r)} comments from video')

    # 总耗时/Total time
    total_time = round(time.time() - start_time, 2)
    print("\nTest completed, total time: {}s".format(total_time))


if __name__ == '__main__':
    api = API(
        email='EMAIL@EXAMPLE.COM',
        password='PASSWORD',
        proxy=None,
    )
    asyncio.run(async_test())
```
