

## 1. 프로젝트 디렉토리 구조 및 에셋 초기 구성
25.12.16.
MiniProject-02의 초기 프로젝트 구조를 확정하고 퍼블리싱 작업을 위한 기본 디렉토리와 정적 에셋 구성을 완료했다.
HTML, 스타일시트, 이미지 리소스를 역할 기준으로 분리해 이후 레이아웃·컴포넌트 확장에 대응 가능한 구조를 마련했다.

```
flowchart TD
    A[MiniProject-02/] --> B[index.html]
    A --> C[img/]
    A --> D[src/]
    A --> E[style/]
    E --> E1[base.css]
    E --> E2[layout.css]
    E --> E3[main.css]
    E --> E4[reset.css]
```
