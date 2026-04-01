# AR-MRD
Provide information related to the paper
MuRumor申请入口，请仔细填写表单：https://docs.google.com/forms/d/e/1FAIpQLSfSxsMh5P2Iv3aPDhk8F_KSsV_h5iAVV_qx_VqqpHnOp24yUQ/viewform?usp=publish-editor


数据集字段说明：
博文数据集
{
  "dataset_schema": {
    "_id": {
      "type": "object",
      "description": "数据库内部唯一标识符（通常为 MongoDB ObjectId），用于区分不同数据样本。"
    },
    "id": {
      "type": "string",
      "description": "微博帖文的唯一标识（微博ID），用于数据索引及跨数据源关联。"
    },
    "tweet_url": {
      "type": "string",
      "description": "微博原始链接，用于访问原始内容或进行数据溯源。"
    },
    "created_at": {
      "type": "string",
      "description": "微博发布时间，包含具体时间与时区信息。"
    },
    "text": {
      "type": "string",
      "description": "微博正文文本内容，是文本模态的主要信息来源。"
    },
    "reposts_count": {
      "type": "integer",
      "description": "转发数量，反映信息传播范围和扩散程度。"
    },
    "comments_count": {
      "type": "integer",
      "description": "评论数量，反映用户互动程度。"
    },
    "attitudes_count": {
      "type": "integer",
      "description": "点赞数量，表示用户对内容的认可程度。"
    },
    "region_name": {
      "type": "string/null",
      "description": "发布地区信息，若为空表示未提供或不可用。"
    },
    "pic_num": {
      "type": "integer",
      "description": "图片数量，表示该帖文中包含的图片总数。"
    },
    "source": {
      "type": "string",
      "description": "发布来源（如客户端或平台类型），用于分析发布渠道。"
    },
    "is_video": {
      "type": "integer",
      "description": "是否包含视频，1 表示包含视频，0 表示不包含。"
    },
    "is_picture": {
      "type": "integer",
      "description": "是否包含图片，1 表示包含图片，0 表示不包含。"
    },
    "video_urls": {
      "type": "object",
      "description": "视频资源链接集合，键值对形式存储视频URL；若为空表示无视频。"
    },
    "pic_urls": {
      "type": "object",
      "description": "图片资源链接集合，通常以 url0、url1 等键标识多张图片。"
    },
    "user": {
      "type": "object",
      "description": "发帖用户的属性信息集合。",
      "fields": {
        "id": {
          "type": "integer",
          "description": "用户唯一标识。"
        },
        "idstr": {
          "type": "string",
          "description": "用户ID的字符串形式。"
        },
        "screen_name": {
          "type": "string",
          "description": "用户昵称。"
        },
        "profile_image_url": {
          "type": "string",
          "description": "用户头像URL。"
        },
        "profile_url": {
          "type": "string",
          "description": "用户主页链接。"
        },
        "verified": {
          "type": "boolean",
          "description": "用户是否为认证账号。"
        },
        "verified_type": {
          "type": "integer",
          "description": "认证类型标识，不同数值对应不同认证类别。"
        },
        "domain": {
          "type": "string",
          "description": "用户个性化域名标识。"
        },
        "weihao": {
          "type": "string",
          "description": "微博号（若存在）。"
        },
        "avatar_large": {
          "type": "string",
          "description": "大尺寸头像链接。"
        },
        "avatar_hd": {
          "type": "string",
          "description": "高清头像链接。"
        },
        "follow_me": {
          "type": "boolean",
          "description": "该用户是否关注当前用户（依赖上下文）。"
        },
        "following": {
          "type": "boolean",
          "description": "当前用户是否关注该账号。"
        },
        "mbrank": {
          "type": "integer",
          "description": "会员等级。"
        },
        "mbtype": {
          "type": "integer",
          "description": "会员类型。"
        },
        "v_plus": {
          "type": "integer",
          "description": "认证增强标识。"
        },
        "planet_video": {
          "type": "boolean",
          "description": "是否具备视频内容相关权限或能力。"
        },
        "icon_list": {
          "type": "array",
          "description": "用户附加图标信息列表。"
        }
      }
    },
    "label": {
      "type": "string",
      "description": "样本标签，用于虚假新闻检测任务，通常包括 rumor（谣言）和 non-rumor（非谣言）。"
    }
  }
}

评论数据集字段
{
  "comment_dataset_schema": {
    "id": {
      "type": "object/integer",
      "description": "评论的唯一标识符，用于区分不同评论样本。在原始数据中可能以 $numberLong 形式存储。",
      "normalized_meaning": "评论ID"
    },
    "created_at": {
      "type": "string",
      "description": "评论发布时间，包含具体时间与时区信息。"
    },
    "user_info": {
      "type": "object",
      "description": "发表评论用户的属性信息集合，用于刻画评论者身份特征、社交属性和账号状态。",
      "fields": {
        "id": {
          "type": "object/integer",
          "description": "评论用户的唯一标识符。"
        },
        "idstr": {
          "type": "string",
          "description": "用户ID的字符串形式。"
        },
        "pc_new": {
          "type": "integer",
          "description": "微博客户端或账号属性的附加标识字段，具体含义依赖平台定义。"
        },
        "screen_name": {
          "type": "string",
          "description": "用户昵称。"
        },
        "profile_image_url": {
          "type": "string",
          "description": "用户头像URL。"
        },
        "profile_url": {
          "type": "string",
          "description": "用户主页链接。"
        },
        "verified": {
          "type": "boolean",
          "description": "用户是否为认证账号。"
        },
        "verified_type": {
          "type": "integer",
          "description": "认证类型编码，不同取值表示不同认证类别。"
        },
        "domain": {
          "type": "string",
          "description": "用户个性化域名标识。"
        },
        "weihao": {
          "type": "string",
          "description": "微博号字段，若为空表示未设置。"
        },
        "avatar_large": {
          "type": "string",
          "description": "用户大尺寸头像链接。"
        },
        "avatar_hd": {
          "type": "string",
          "description": "用户高清头像链接。"
        },
        "follow_me": {
          "type": "boolean",
          "description": "该用户是否关注当前登录用户，通常依赖抓取环境。"
        },
        "following": {
          "type": "boolean",
          "description": "当前登录用户是否关注该评论用户。"
        },
        "mbrank": {
          "type": "integer",
          "description": "会员等级。"
        },
        "mbtype": {
          "type": "integer",
          "description": "会员类型。"
        },
        "v_plus": {
          "type": "integer/null",
          "description": "认证增强标识，可能为空。"
        },
        "fansIcon": {
          "type": "object",
          "description": "粉丝标识信息对象，用于描述粉丝身份或会员图标相关属性。",
          "fields": {
            "fans_uid": {
              "type": "object/integer",
              "description": "粉丝用户ID。"
            },
            "val": {
              "type": "integer",
              "description": "粉丝标识数值字段。"
            },
            "member_rank": {
              "type": "integer",
              "description": "会员等级标识。"
            },
            "svip": {
              "type": "integer",
              "description": "是否为超级会员标识。"
            },
            "vvip": {
              "type": "integer",
              "description": "是否为更高级别会员标识。"
            },
            "lighting": {
              "type": "boolean",
              "description": "是否启用特殊点亮标识。"
            },
            "icon_url": {
              "type": "string",
              "description": "粉丝图标URL。"
            },
            "uid": {
              "type": "object/integer",
              "description": "用户ID。"
            },
            "name": {
              "type": "string",
              "description": "粉丝标识名称。"
            }
          }
        },
        "planet_video": {
          "type": "boolean",
          "description": "是否具备视频相关能力或权限标识。"
        },
        "description": {
          "type": "string",
          "description": "用户个人简介。"
        },
        "location": {
          "type": "string",
          "description": "用户所在地信息。"
        },
        "gender": {
          "type": "string",
          "description": "用户性别标识，通常 m 表示男性，f 表示女性。"
        },
        "followers_count": {
          "type": "integer",
          "description": "粉丝数。"
        },
        "followers_count_str": {
          "type": "string",
          "description": "粉丝数的字符串形式。"
        },
        "friends_count": {
          "type": "integer",
          "description": "关注数，即该用户关注的其他账号数量。"
        },
        "statuses_count": {
          "type": "integer",
          "description": "该用户发布的微博总数。"
        },
        "url": {
          "type": "string",
          "description": "用户外部主页或博客链接。"
        },
        "svip": {
          "type": "integer",
          "description": "超级会员标识。"
        },
        "vvip": {
          "type": "integer",
          "description": "高级会员标识。"
        },
        "cover_image_phone": {
          "type": "string",
          "description": "移动端封面图片链接。"
        },
        "icon_list": {
          "type": "array",
          "description": "用户附加图标信息列表。"
        }
      }
    },
    "like_count": {
      "type": "integer",
      "description": "该评论获得的点赞数，用于衡量评论互动热度。"
    },
    "text": {
      "type": "string",
      "description": "评论正文内容，是评论语义分析、立场分析和传播分析的主要文本信息。"
    },
    "orignal_tweet_id": {
      "type": "object/integer",
      "description": "该评论所对应的原始微博ID，用于将评论与源帖文进行关联。原始字段名中 orignal 可能是 original 的拼写变体。",
      "normalized_meaning": "原帖ID"
    }
  }
}
