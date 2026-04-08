# Azure OpenAI / Microsoft Foundry Kurulumu

Bu rehber, kurs içindeki örnekleri Azure OpenAI veya Microsoft Foundry üzerinden çalıştırmak isteyenler için Türkçe, sadeleştirilmiş bir kurulum akışı sunar.

## Ön koşullar

Kuruluma başlamadan önce şunlara ihtiyacınız var:

- Azure hesabı ve aktif bir abonelik
- .NET 10 SDK veya üzeri
- Otomatik kurulum kullanacaksanız Azure Developer CLI (`azd`)

## Yol 1: Otomatik kurulum

İlk kez Azure tarafını hazırlıyorsanız en kolay yol budur.

```powershell
./setup.ps1
```

Bu komut temel olarak şunları yapar:
- gerekli Azure kaynaklarını oluşturur
- `gpt-5-mini` ve `text-embedding-3-small` dağıtımlarını hazırlar
- ortak `user-secrets` yapılandırmasını ayarlar

Kurulum bittiğinde örnek bir proje altında aşağıdaki gibi doğrulama yapabilirsiniz:

```powershell
cd samples/CoreSamples/BasicChat-01MEAI
dotnet run app.cs
```

## Yol 2: Elinizde zaten Azure kaynakları varsa

Halihazırda bir Azure OpenAI kaynağınız varsa, yalnızca gizli yapılandırmaları tanımlamanız yeterlidir.

### setup-secrets.ps1 ile

```powershell
./setup-secrets.ps1 -Endpoint "https://my-resource.openai.azure.com/"
```

### dotnet user-secrets ile

```powershell
dotnet user-secrets set --id genai-beginners-dotnet "AzureOpenAI:Endpoint" "https://my-resource.openai.azure.com/"
dotnet user-secrets set --id genai-beginners-dotnet "AzureOpenAI:Deployment" "gpt-5-mini"
dotnet user-secrets set --id genai-beginners-dotnet "AzureOpenAI:EmbeddingDeployment" "text-embedding-3-small"
```

## Yol 3: Manuel Foundry kurulumu

Kurulum sürecini anlamak istiyorsanız Azure AI Foundry portalı üzerinden ilerleyebilirsiniz.

Temel adımlar:
1. Yeni bir Foundry projesi oluşturun.
2. `gpt-5-mini` modelini dağıtın.
3. RAG örnekleri için `text-embedding-3-small` dağıtın.
4. Endpoint ve deployment bilgilerini alın.
5. Bu değerleri `user-secrets` içine yazın.

## Doğrulama

Aşağıdaki komut, temel ayarların yüklenip yüklenmediğini hızlıca gösterir:

```powershell
dotnet user-secrets list --id genai-beginners-dotnet
```

Ardından bir örnek uygulamayı çalıştırarak zinciri uçtan uca test edin.

## Ek yapılandırmalar

Bazı örneklerde aşağıdaki ek gizli bilgiler gerekebilir:
- `AIFoundry:Endpoint`
- `AIFoundry:TenantId`
- `AzureAISearch:Endpoint`
- `AzureAISearch:Key`
- `AzureSpeech:Key`
- `AzureSpeech:Region`

## Temizlik

Kurs bittiğinde kaynakları kapatmak için:

```powershell
./cleanup.ps1
```

## Medium notu

Bu dosya, orijinal kurulum rehberinin Türkçe ve daha okunabilir bir karşılığıdır. Ayrı Medium reposunda teknik kurulum yazısı olarak ya bağımsız yayınlanabilir ya da ilk dersin ek kaynağı olarak verilebilir.
