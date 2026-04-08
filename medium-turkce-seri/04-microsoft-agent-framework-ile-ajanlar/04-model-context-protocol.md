# Model Context Protocol (MCP)

MCP, agent ve AI araç ekosisteminde standartlaşma problemine verilen güçlü bir cevaptır. Basit ifadeyle, modellerin ve ajanların dış araçlarla ortak bir protokol üzerinden konuşmasını sağlar.

## MCP nedir?

Model Context Protocol:
- araçları ve kaynakları standart biçimde sunar
- agent'ların farklı sistemlerle daha düzenli bağ kurmasını sağlar
- tek seferlik özel entegrasyon ihtiyacını azaltır

Bu yüzden agent dünyasında “ortak bağlantı standardı” gibi düşünülebilir.

## Neden önemli?

Araç ekosistemi büyüdükçe her servis için ayrı özel entegrasyon yazmak maliyetli olur. MCP sayesinde aynı fikir çatısı altında:
- GitHub
- Hugging Face
- dosya sistemleri
- şirket içi servisler

gibi kaynaklara daha düzenli erişim sağlanabilir.

## 1. Kısım: MCP bileşenleri

Temel iki rol vardır:
- **MCP server**: araçları ve kaynakları sunar
- **MCP client**: bu araçlara bağlanır ve kullanır

## 2. Kısım: MCP server'a bağlanmak

Bir ajan, MCP üzerinden dış dünyaya kontrollü erişim kazanır. Bu da özellikle tool çeşitliliği arttığında yönetilebilirliği yükseltir.

## 3. Kısım: Yaygın server örnekleri

GitHub ve Hugging Face gibi örnekler, MCP'nin pratikte neden değerli olduğunu gösterir. Çünkü geliştirici için tekrar kullanılabilir bir entegrasyon modeli sunar.

## 4. Kısım: Lokal modellerle MCP

MCP yalnızca bulut tabanlı ajanlarla sınırlı değildir. Ollama gibi yerel model akışlarında da dış araçlar için ortak bir katman olarak değerlendirilebilir.

## 5. Kısım: Kendi MCP server'ını yazmak

Kurum içi sistemler için özel MCP server yazarak şirketin veri ve araç katmanını ajanlara standart biçimde açabilirsiniz. Bu özellikle büyük organizasyonlarda önemli bir mimari avantajdır.

## 6. Kısım: Güvenlik

MCP kullanırken mutlaka düşünülmesi gereken başlıklar:
- veri mahremiyeti
- kimlik doğrulama
- yetki sınırları
- güvenilmeyen server'lara karşı dikkat

## 7. Kısım: Ne zaman MCP kullanılmalı?

Aşağıdaki durumlarda güçlü adaydır:
- çok sayıda dış araç varsa
- tekrar kullanılabilir entegrasyon hedefleniyorsa
- multi-agent yapı kuruluyorsa
- kurum içi araç katmanı standartlaştırılmak isteniyorsa

## Sonuç

MCP, agent mimarisinin ölçeklenebilir tarafını güçlendirir. Bu yüzden ayrı bir konu değil, ajan ekosisteminin temel bileşenlerinden biri olarak düşünülmelidir.

## İlgili örnekler

- `samples/PracticalSamples/`
- `samples/CoreSamples/MCP-01-HuggingFace/`
- `samples/CoreSamples/MCP-02-HuggingFace-Ollama/`
