# React Component Life Cycle

React, bileşenlerin hayat döngüsü boyunca belirli aşamalarda çalışan özel metotlar sağlar. Bu metotlar, bir bileşenin oluşturulması, güncellenmesi ve kaldırılması gibi aşamalarda kontrol sağlar. İşte React component life cycle'ı anlamak için önemli bilgiler:

## Nedir?

React bileşen life cycle'ı, bir bileşenin oluşturulma, güncellenme ve kaldırılma aşamalarında çalışan metotları içerir. Bu metotlar, özel işlemleri gerçekleştirmek ve bileşenin davranışını kontrol etmek için kullanılır.

## Ne İşe Yarar?

- **Oluşturma (Mounting) ComponentDidMount Evresi**
  - `constructor`: Bileşen oluşturulduğunda ilk olarak çalışan yapıcı metottur.
  - `render`: Bileşenin arayüzünü oluşturan metottur.
  - `componentDidMount`: Bileşenin DOM'a eklenmesinden sonra çalışan metottur. API çağrıları ve başlangıç işlemleri için kullanışlıdır.

- **Güncelleme (Updating) ComponentDidUpdate Evresi**
  - `render`: Bileşen güncellendiğinde tekrar çalışan metottur.
  - `componentDidUpdate`: Bileşen güncellendikten sonra çalışan metottur. Önceki ve mevcut durumu karşılaştırarak işlemler gerçekleştirmek için kullanılır.

- **Kaldırma (Unmounting) componentWillUnmount Evresi**
  - `componentWillUnmount`: Bileşen kaldırılmadan önce çalışan metottur. Temizlik işlemleri için kullanışlıdır. Kullanılmadığı takdirde bazı sızıntılar olabilir ve component işlemde olmasa bile arka planda bir takım işler yapılmaya devam edebilir.

## Avantajları

- **Daha Kontrollü İşlemler:** Hayat döngüsü metotları, bileşenin her aşamasında özel işlemler gerçekleştirmenize olanak tanır.
- **Optimizasyon:** Performans ve bellek yönetimi için hayat döngüsü metotları kullanılarak optimize edilmiş bileşenler oluşturabilirsiniz.

## Kullanım Örnekleri

```jsx
import React, { Component } from 'react';

class ExampleComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  componentDidMount() {
    console.log('Component oluşturuldu');
    // API çağrıları, abonelikler açma, başlangıç işlemleri
  }

  componentDidUpdate(prevProps, prevState) {
    console.log('Component güncellendi');
    // Önceki ve mevcut durumu karşılaştırarak işlemler
  }

  componentWillUnmount() {
    console.log('Component kaldırıldı');
    // Abonelikleri kapatma, temizleme işlemleri
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Arttır
        </button>
      </div>
    );
  }
}

export default ExampleComponent;
