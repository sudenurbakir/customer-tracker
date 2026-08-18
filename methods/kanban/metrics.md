# Kanban Metrics

Bu projede geliştirme aşaması başladığında aşağıdaki metrikler takip edilecektir.

## Takip Edilecek Metrikler

| Metrik         | Açıklama                                      | Ne İşe Yarar?                              |
|----------------|-----------------------------------------------|--------------------------------------------|
| Cycle Time     | Bir işe başlandıktan sonra bitene kadar geçen süre | Gerçek çalışma hızını gösterir            |
| Lead Time      | Bir işin To Do’ya girdiği andan Done’a kadar geçen süre | Toplam teslim süresini gösterir           |
| Throughput     | Belirli bir sürede biten iş sayısı            | Ne kadar iş teslim edildiğini gösterir    |
| WIP            | Aynı anda In Progress’te olan iş sayısı       | Aşırı yüklenmeyi engeller                  |

## Nasıl Takip Edeceğiz?

- Jira’daki **Control Chart** → Cycle Time için
- Jira’daki **Cumulative Flow Diagram** → Akış ve birikme için
- Haftalık olarak Throughput (biten iş sayısı) kontrol edilecek

## Hedef

- Cycle Time’ı mümkün olduğunca kısa tutmak
- In Progress’te iş birikmesini engellemek
- Düzenli ve öngörülebilir teslim akışı sağlamak
