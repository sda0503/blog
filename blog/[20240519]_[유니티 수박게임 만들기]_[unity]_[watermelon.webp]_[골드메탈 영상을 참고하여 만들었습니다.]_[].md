# 유니티를 사용하여 수박게임 만들기1

준비물 : 유니티, 비주얼스튜디오(비주얼스튜디오 코드 아님), 자료이미지(자료이미지의 경우 포토샵을 이용하여 제작 하였음, 미리캔버스나, 아래의 링크를 통해서 다운로드 받으면 됩니다.)

[이미지 다운로드](https://www.youtube.com/redirect?event=video_description&amp;redir_token=QUFFLUhqbi1QLWdIb2VpX1NCUXpOdG9kb2dia3lkeE5Sd3xBQ3Jtc0tuMzlfQkFrMk9sMnY3aDJDRG43RU5aUElrS3hJbXVfRWNhVk1McUhmRDRsQ0xUbU9EbGRXVDJKaWVKQzFBLTBxZGo0NTFSSy1WdVlWNXBkRm9jckNLcUllTzU3MjB0WEpIM0V5MEhZRXFRQk9UYnY3dw&amp;q=https%3A%2F%2Fwww.goldmetal.co.kr%2Funity%2Fpackages%2FDongleFamily_Assets_Pack.unitypackage&amp;v=eQPp0QTz4JM) (골드메탈의 에셋)

과정1.환경 셋팅 (벽만들고, 배경 이미지 추가하기)

과정2.오브젝트 움직임 추가하기 아래의 스크립트 참조하기 (골드메탈 스크립트와 다를 수 있음)

C# 코드: 과일 오브젝트에 적용할 C# 스크립트
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class prefabs : MonoBehaviour
{
    public bool isDrag = false;
    Rigidbody2D rigid;

    void Awake()
    {
        rigid = GetComponent<Rigidbody2D>();
    }

    void Update()
    {
        if (isDrag)
        {
            Vector3 mousePos = Camera.main.ScreenToWorldPoint(Input.mousePosition);
            float Lborder = -2.8f + transform.localScale.x / 2f;
            float Rborder = 1.3f + transform.localScale.x / 2f;

            mousePos.z = 0;
            mousePos.y = 4;
            if (mousePos.x < Lborder)
            {
                mousePos.x = Lborder;
            }
            else if (mousePos.x > Rborder)
            {
                mousePos.x = Rborder;
            }
            transform.position = Vector3.Lerp(transform.position, mousePos, 0.2f);
        }
    }

    public void Drag()
    {
        isDrag = true;
    }

    public void Drop()
    {
        isDrag=false;
        rigid.simulated = true;
    }
}

```

[골드메탈 수박게임 유튜브 영상](https://www.youtube.com/watch?v=eQPp0QTz4JM&list=PLO-mt5Iu5TeajtA5UQT7_2UjB7_dkGagU)