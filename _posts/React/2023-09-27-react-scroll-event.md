홈페이지 우측 하단에 고정되어 따라다니는 플로팅 버튼을 만들었습니다.

그런데 이 플로팅 버튼으로인해 홈페이지 최하단 푸터의 일부 정보가 보이지 않는 현상이 있었습니다. 이를 방지하고자 스크롤을 일정 이상 내렸을 경우 플로팅 버튼이 사라지는 효과를 넣었습니다.

부드럽게 보이기 위해 페이드인, 페이드아웃 애니메이션도 추가해주었습니다.

body의 전체 스크롤 높이를 이용하여 EventListener를 붙이는 간단한 방법입니다.

```javascript
export const FloatingButton = () => {
  const [isVisible, setVisible] = useState < boolean > true;

  useEffect(() => {
    const handleScroll = (e: Event) => {
      if (window.scrollY > document.body.scrollHeight * 0.85) {
        setVisible(false);
      } else {
        setVisible(true);
      }
    };
    window.addEventListener("scroll", handleScroll);

    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  }, []);

  return <Block isVisible={isVisible} />;
};

const FadeIn = keyframes`
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
`;

const FadeOut = keyframes`
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
`;

const Block =
  styled.div <
  { isVisible: boolean } >
  `
  position: fixed;
  right: 40px;
  bottom: 50px;
  visibility: ${(props) => (props.isVisible ? "visible" : "hidden")};
  animation: ${(props) =>
    props.isVisible ? FadeIn : FadeOut} 0.5s ease-in-out;
  transition: visibility 0.5s ease-in-out;
  z-index: 1;
`;
```
