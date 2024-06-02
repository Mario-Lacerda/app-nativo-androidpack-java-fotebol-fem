# Desafio Dio - App Nativo Sobre Futebol Feminino com Android Jetpack e Java



### **Projeto: App Nativo Sobre Futebol Feminino com Android Jetpack e Java**

Este projeto tem como objetivo criar um aplicativo nativo para Android que forneça informações abrangentes sobre futebol feminino, utilizando o Android Jetpack e Java. O aplicativo incluirá recursos como notícias, resultados, classificações e perfis de jogadoras.

#### **Requisitos**

- Android Studio
- Conhecimento básico de Java e Android Development
- Conhecimento de Android Jetpack



#### **Estrutura do Projeto**

O projeto será estruturado usando o Android Jetpack, que fornece bibliotecas e componentes para o desenvolvimento de aplicativos Android.



#### **Recursos do Aplicativo**

- **Notícias:** Exibe as últimas notícias sobre futebol feminino de fontes confiáveis.
- **Resultados:** Mostra os resultados dos jogos recentes e futuros.
- **Classificações:** Exibe as classificações das principais ligas e torneios de futebol feminino.
- **Jogadoras:** Fornece perfis detalhados de jogadoras de futebol feminino, incluindo estatísticas e informações biográficas.



**Código**

#### **MainActivity.java**

java

```java
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.Fragment;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Fragment fragment = new NewsFragment();
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.fragment_container, fragment)
                .commit();
    }
}
```



#### **NewsFragment.java**

java

```java
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;

import androidx.fragment.app.Fragment;
import androidx.recyclerview.widget.LinearLayoutManager;
import androidx.recyclerview.widget.RecyclerView;

public class NewsFragment extends Fragment {

    private RecyclerView recyclerView;
    private NewsAdapter adapter;

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        View view = inflater.inflate(R.layout.fragment_news, container, false);

        recyclerView = view.findViewById(R.id.recycler_view);
        recyclerView.setLayoutManager(new LinearLayoutManager(getContext()));

        adapter = new NewsAdapter(getNewsItems());
        recyclerView.setAdapter(adapter);

        return view;
    }

    private List<NewsItem> getNewsItems() {
        List<NewsItem> newsItems = new ArrayList<>();

        // Adicione os itens de notícias aqui

        return newsItems;
    }
}
```



#### **NewsAdapter.java**

java

```java
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.TextView;

import androidx.recyclerview.widget.RecyclerView;

import java.util.List;

public class NewsAdapter extends RecyclerView.Adapter<NewsAdapter.ViewHolder> {

    private List<NewsItem> newsItems;

    public NewsAdapter(List<NewsItem> newsItems) {
        this.newsItems = newsItems;
    }

    @Override
    public ViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        View view = LayoutInflater.from(parent.getContext()).inflate(R.layout.item_news, parent, false);
        return new ViewHolder(view);
    }

    @Override
    public void onBindViewHolder(ViewHolder holder, int position) {
        NewsItem newsItem = newsItems.get(position);

        holder.titleTextView.setText(newsItem.getTitle());
        holder.descriptionTextView.setText(newsItem.getDescription());
    }

    @Override
    public int getItemCount() {
        return newsItems.size();
    }

    public class ViewHolder extends RecyclerView.ViewHolder {

        private TextView titleTextView;
        private TextView descriptionTextView;

        public ViewHolder(View itemView) {
            super(itemView);

            titleTextView = itemView.findViewById(R.id.title_text_view);
            descriptionTextView = itemView.findViewById(R.id.description_text_view);
        }
    }
}
```



### **Conclusão**

Este projeto fornece um modelo básico para criar um aplicativo nativo para Android que oferece informações abrangentes sobre futebol feminino. Ele pode ser expandido e personalizado para atender a requisitos específicos.
