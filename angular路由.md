### app.module.ts
```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import {FormsModule,ReactiveFormsModule}  from '@angular/forms'
import {StorageService} from './services/storage.service'
import { HttpClientModule} from '@angular/common/http'
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { FirstConponentComponent } from './first-conponent/first-conponent.component';
import { SecondComponentComponent } from './second-component/second-component.component';
import { ThirdComponentComponent } from './third-component/third-component.component';
import { LiftComponent } from './lift/lift.component';
import { ContentComponent } from './content/content.component';
import { NewsDetailComponent } from './news-detail/news-detail.component';
import { HtmlComponent } from './second-component/html/html.component';
import { JavascriptComponent } from './second-component/javascript/javascript.component';
import { CssComponent } from './second-component/css/css.component';
@NgModule({
  declarations: [
    AppComponent,
    FirstConponentComponent,
    SecondComponentComponent,
    ThirdComponentComponent,
    LiftComponent,
    ContentComponent,
    NewsDetailComponent,
    HtmlComponent,
    JavascriptComponent,
    CssComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule,
    HttpClientModule,
    ReactiveFormsModule
  ],
  providers: [StorageService],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

### app-routing.modules.ts
```typescript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { FirstConponentComponent } from './first-conponent/first-conponent.component';
import { SecondComponentComponent } from './second-component/second-component.component';
import { ThirdComponentComponent } from './third-component/third-component.component';
import { LiftComponent } from './lift/lift.component';
import { ContentComponent } from './content/content.component';
import { NewsDetailComponent } from './news-detail/news-detail.component';
import { HtmlComponent } from './second-component/html/html.component';
import { JavascriptComponent } from './second-component/javascript/javascript.component';
import { CssComponent } from './second-component/css/css.component';

//配置路由信息
const routes:Routes = [
  {
    path:'first',
    component:FirstConponentComponent
  },
  {
    path:'second',
    component:SecondComponentComponent,
    children:[
      {
        path:'html',
        component:HtmlComponent
      },
      {
        path:'javascript',
        component:JavascriptComponent
      },
      {
        path:'css',
        component:CssComponent
      },
      {
        path:'**',
        redirectTo:'html',
      },
    ]
  },
  {
    path:'third',
    component:ThirdComponentComponent
  },
  {
    path:'lift',
    component:LiftComponent
  },
  {
    path:'news',
    component:ContentComponent
  },
  {
    path:'newsDetail/:id',
    component:NewsDetailComponent
  },
  {
    path:'**',
    redirectTo:'first',
  },
]

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }

```

### app.html
```html
<ul class="rouetr">
    <a [routerLink]="[ '/first']" class="link" routerLinkActive="active">组件一</a>
    <a [routerLink]="[ '/second']" class="link" routerLinkActive="active">组件二</a>
    <a [routerLink]="[ '/third']" class="link" routerLinkActive="active">组件三</a>
    <a [routerLink]="[ '/lift']" class="link" routerLinkActive="active">组件四</a>
    <a [routerLink]="[ '/news']" class="link" routerLinkActive="active">新闻</a>
</ul>

<router-outlet></router-outlet>
```

### second.html
```html
<div class="wrapper">
    <ul class="left">
        <li [routerLink]="[ '/second/html']" class="link" routerLinkActive="active">组件一</li>
        <li [routerLink]="[ '/second/javascript']" class="link" routerLinkActive="active">组件二</li>
        <li [routerLink]="[ '/second/css']" class="link" routerLinkActive="active">组件三</li>
    </ul>
    <div class="right">
        <router-outlet></router-outlet>
    </div>
</div>
```
