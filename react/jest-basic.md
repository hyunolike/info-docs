## JEST
> [참고자료](https://inpa.tistory.com/entry/JEST-%F0%9F%93%9A-jest-%EB%AC%B8%EB%B2%95-%EC%A0%95%EB%A6%AC)
- 페이스북에서 개발 >> 테스팅 라이브러리
- JSET >> Test Runner + Test Mathcher + Test Mock 프레임웍 지원 
- `create-react-app` >> 프로젝트 내장됨!

### 문법
- `describe`: 테스트 그룹 묶어주는 역할 / 콜백함수 내에 테스트에 쓰일 가짜 변수, 객체들 선언 >> 일회용 사용 가능
- `it`: describe의 작은 단위테스트
- `toXX`: `Test Mathcher` 

#### `Counter.jsx` - [참고자료](https://www.zerocho.com/category/React/post/583231469a87ec001834a0ec)
```javascript
import React, { Component } from 'react';

export default class Counter extends Component {
  state = {
    value: 0,
    title: '',
  }

  changeTitle = (e) => {
    this.setState(() => ({ title: e.target.value }));
  }

  increment = () => {
    this.setState(prevState => ({ value: prevState.value + 1 }));
  };

  render() {
    return (
      <div>
        <input value={this.state.title} id="title" onChange={this.changeTitle} />
        <b>{this.state.value}</b>
        <button id="up" onClick={this.increment}>증가</button>
      </div>
    );
  }
}
```

#### `Counter-test.jsx`
```javascript
import React from 'react';
import Counter from './counter.jsx';
import { shallow, configure } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';
configure({ adapter: new Adapter() });

describe('<Counter />', () => {
  it('성공적으로 렌더링되어야 합니다.', () => {
    const wrapper = shallow(<Counter />);
    expect(wrapper.length).toBe(1);
  });

  it('타이틀 인풋이 렌더링되어야 합니다.', () => {
    const wrapper = shallow(<Counter />);
    expect(wrapper.find('#title').length).toEqual(1);
  });

  it('타이틀이 변경되어야 합니다.', () => {
    const wrapper = shallow(<Counter />);
    wrapper.find('#title').simulate('change', { target: { value: '값' } });
    expect(wrapper.state().title).toBe('값');
  });

  it('숫자가 올라가야 합니다.', () => {
    const wrapper = shallow(<Counter />);
    wrapper.find('#up').simulate('click');
    wrapper.find('#up').simulate('click');
    expect(wrapper.state().value).toBeLessThan(1);
  });
});
```

### [실습 참고자료](https://jinminkim-50502.medium.com/testing-tool-jest-756bbc0a7a16)
