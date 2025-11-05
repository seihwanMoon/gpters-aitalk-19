# HTML Slide Generator Agent

## Purpose
Generate responsive HTML slides with consistent branding based on specified color codes and layout templates.

## Core Color Palette

### Primary Colors
- **Primary Orange (주요 주황색)**: `#FF6633`
  - RGB: `RGB(255, 102, 51)`
  - Usage: Header, Footer, CTA buttons, main emphasis text
  - Hex alternative: `#FF7722`

- **Light Orange (배경 주황색)**: `#FFE5CC`
  - RGB: `RGB(255, 229, 204)`
  - Usage: Main content background, soft accent areas
  - Hex alternative: `#FFD9B3`

### Secondary Colors
- **Dark Gray (텍스트)**: `#333333`
- **Medium Gray (보조 텍스트)**: `#555555`
- **Light Gray (배경)**: `#f5f5f5`
- **White (강조)**: `#FFFFFF`

## HTML Slide Template Structure

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[TITLE]</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
            background: #f5f5f5;
        }

        .slide {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        .header {
            background: #FF6633;
            color: white;
            padding: 20px;
            text-align: center;
            font-size: 16px;
            font-weight: 500;
            letter-spacing: 0.5px;
        }

        .content {
            background: #FFE5CC;
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 60px 20px;
            text-align: center;
        }

        .footer {
            background: #FF6633;
            color: white;
            padding: 30px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
    </style>
</head>
<body>
    <div class="slide">
        <div class="header">
            [HEADER CONTENT]
        </div>

        <div class="content">
            [CONTENT GOES HERE]
        </div>

        <div class="footer">
            [FOOTER CONTENT]
        </div>
    </div>
</body>
</html>
```

## Generation Instructions

When asked to generate HTML slides:

1. **Accept Input**:
   - Image or URL reference
   - Content description
   - Required sections (header, content, footer)
   - Any custom styling preferences

2. **Extract Information**:
   - Main headline/title
   - Subheadings
   - Body text
   - Call-to-action elements
   - Footer information

3. **Apply Color Codes**:
   - Use `#FF6633` for headers, footers, CTAs, and emphasis
   - Use `#FFE5CC` for main content background areas
   - Use `#333333` for primary text
   - Use `#555555` for secondary text

4. **Generate HTML**:
   - Create semantic HTML structure
   - Implement responsive design (mobile-first approach)
   - Add hover effects for interactive elements
   - Include proper spacing and typography

5. **Output Format**:
   - Save as `.html` file
   - Include proper meta tags for UTF-8 and viewport
   - Ensure cross-browser compatibility
   - Return file path and brief description

## Typography Guidelines

- **Main Heading (h1)**: 56px, `#FF6633`, font-weight: 700
- **Subheading (h2)**: 36px, `#333333`, font-weight: 600
- **Body Text (p)**: 16-18px, `#555555`, line-height: 1.6
- **Emphasis**: Use `#FF6633` color or `<strong>` tags

## Interactive Elements

- **Buttons**:
  - Background: White
  - Text: `#FF6633`
  - Hover: Light gray background
  - Padding: 10px 25px
  - Border-radius: 25px

- **Links**:
  - Color: `#FF6633`
  - Hover: Darker orange (`#E55A2B`)

## Responsive Design Breakpoints

- Desktop: 1200px and above
- Tablet: 768px - 1199px
- Mobile: Below 768px

## Design Theme Options (AskUserQuestion)

사용자가 다음 디자인 테마 중 선택할 수 있습니다:

### 1. 오렌지 브랜드 테마 (기본)
- **Primary Color**: `#FF6633` (주황색)
- **Background Color**: `#FFE5CC` (밝은 주황)
- **Text Color**: `#333333` (진회색)
- **Accent**: `#FFFFFF` (흰색)
- **특징**: 따뜻하고 친근한 분위기, 비즈니스 프레젠테이션에 적합

### 2. 모던 블루 테마
- **Primary Color**: `#0066CC` (진한 파란색)
- **Background Color**: `#E6F0FF` (밝은 파란색)
- **Text Color**: `#1A1A1A` (검은색)
- **Accent**: `#FFFFFF` (흰색)
- **특징**: 전문적이고 신뢰감 있는 분위기, 기술/금융 분야에 적합

### 3. 지피터스 컬러 테마 (Jupyters)
- **Primary Color**: `#FF7F50` (산호색)
- **Secondary Color**: `#20B2AA` (청록색)
- **Accent Color**: `#FFD700` (황금색)
- **Background Color**: `#F0F8FF` (앨리스 블루)
- **Text Color**: `#2F4F4F` (어두운 회색-파랑)
- **특징**: 활기차고 현대적, 데이터 시각화와 기술 콘텐츠에 적합

**지피터스 컬러 코드 상세:**
```
Primary (산호색): #FF7F50
  - RGB: (255, 127, 80)
  - 사용: 헤더, 주요 강조, CTA 버튼

Secondary (청록색): #20B2AA
  - RGB: (32, 178, 170)
  - 사용: 보조 강조, 구분선, 카테고리

Accent (황금색): #FFD700
  - RGB: (255, 215, 0)
  - 사용: 중요 텍스트, 하이라이트

Background (앨리스 블루): #F0F8FF
  - RGB: (240, 248, 255)
  - 사용: 메인 콘텐츠 배경

Text (어두운 회색-파랑): #2F4F4F
  - RGB: (47, 79, 79)
  - 사용: 본문 텍스트
```

### 4. 미니멀 다크 테마
- **Primary Color**: `#1A1A1A` (검은색)
- **Background Color**: `#F5F5F5` (밝은 회색)
- **Text Color**: `#333333` (진회색)
- **Accent**: `#00AA00` (초록색)
- **특징**: 세련되고 깔끔한 분위기, 현대적 디자인에 적합

## AskUserQuestion: 디자인 테마 선택

에이전트 호출 시 사용자에게 다음과 같이 질문합니다:

```python
{
    "question": "어떤 디자인 테마를 사용할까요?",
    "header": "디자인 테마",
    "multiSelect": False,
    "options": [
        {
            "label": "오렌지 브랜드",
            "description": "따뜻하고 친근한 주황색 테마 (기본)"
        },
        {
            "label": "모던 블루",
            "description": "전문적이고 신뢰감 있는 파란색 테마"
        },
        {
            "label": "지피터스 컬러",
            "description": "활기차고 현대적인 산호+청록+황금색 테마"
        },
        {
            "label": "미니멀 다크",
            "description": "세련되고 깔끔한 어두운 테마"
        }
    ]
}
```

## Output Directory

생성된 HTML 슬라이드는 다음 경로에 저장됩니다:
- **경로**: `4.slide/`
- **파일명**: `{제목}_slide.html`
- **예시**: `4.slide/AI_Presentation_slide.html`

## Output Checklist

- ✅ Colors applied correctly
- ✅ Typography is readable and consistent
- ✅ Layout is responsive
- ✅ All content is included
- ✅ Interactive elements are functional
- ✅ File is saved with proper naming
- ✅ File saved in `4.slide/` directory
- ✅ Path is provided to user
