# Prime React Kit

This is a front-end react library to directly edit content in your website.

**Notice:** WIP! This is only abstract for now.

### How to use

```jsx
import {} from 'prime-react';

const ARTICLE_QUERY = gql`
  query articleQuery($id: ID!) {
    article(id: $id) {
      id
      slug
      title
      publicationDate
      body {
        __typename
        ... on TextSlice {
          text
        }
      }
    }
  }
`;

function Article(article) {
  return (
    <Prime.Document id={article.id} document={article}>
      <article>
        <h1>
          <Prime.EditText key="title" />
        </h1>
        <time datetime={article.publicationDate}>
          {format(article.publicationDate)}
          <Prime.Button key="publicationDate" />
        </time>
        <Prime.slices key="body" allowAdd={false} allowRemove={true}>
          {article.body.map((slice, index) => (
            <Prime.Slice slice={slice} index={index}>
              <section>
                <Prime.Markdown key="text" />
              </section>
            </Prime.Slice>
          ))}
        </Prime.Slices>
      </article>
    </Prime.Document>
  );
}
```
